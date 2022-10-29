# definition

```
class Point:
    x: int
    y: int
```


```
import pickle
from collections.abc import Callable
from typing import NewType

MyObject = NewType('UserId', Callable[[], str])


class Serializer(object):

    def __init__(self, compression=False, compression_level=6, use_zlib: bool=False,
                 pickle_protocol=pickle.HIGHEST_PROTOCOL):
        """
        Initializer, expected arguments:
        - compression - True, means zip compression is going to be used
        - compression_level - compresson level
        - use_zlib - True, means using zlib library
        """
        self.comp = compression
        self.comp_level = compression_level
        self.use_zlib = use_zlib
        self.pickle_protocol = pickle_protocol or pickle.HIGHEST_PROTOCOL
        if self.comp:
            if self.use_zlib and zlib is None:
                raise ConfigurationError('use_zlib specified, but zlib module '
                                         'not found.')
            elif gzip is None:
                raise ConfigurationError('gzip module required to enable '
                                         'compression.')

    def _serialize(self, data: str) -> str:
        """Serialize given data to pickle reprezentation"""
        return pickle.dumps(data, self.pickle_protocol)

    def _deserialize(self, data: str) -> Callable[[], str]:
        """Deserialize pickled object to its original state"""
        return pickle.loads(data)

    def serialize(self, data: Callable[[], str]):
        data = self._serialize(data)
        if self.comp:
            if self.use_zlib:
                data = zlib.compress(data, self.comp_level)
            else:
                data = gzip_compress(data, self.comp_level)
        return data

    def deserialize(self, data: MyObject) -> str:
        if self.comp:
            if not is_compressed(data):
                logger.warning('compression enabled but message data does not '
                               'appear to be compressed.')
            elif self.use_zlib:
                data = zlib.decompress(data)
            else:
                data = gzip_decompress(data)
        return self._deserialize(data)
```

Usage

```
data = {"key1": "some value"}
s = Serializer()
serialized_data = s.serialize(data)
s.deserialize(serialized_data)
```

