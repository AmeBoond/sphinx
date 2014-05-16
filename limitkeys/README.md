# limitkeys
--
    import "github.com/Clever/sphinx/limitkeys"


## Usage

#### func  NewHeaderLimitKeys

```go
func NewHeaderLimitKeys(config interface{}) ([]LimitKey, error)
```
NewHeaderLimitKeys creates a slice of headerLimitKeys that keys on the named
request header

#### func  NewIPLimitKeys

```go
func NewIPLimitKeys(config interface{}) ([]LimitKey, error)
```
NewIPLimitKeys creates a slice of ipLimitKeys that returns a key based on
request remoteaddr

#### type EmptyKeyError

```go
type EmptyKeyError struct {
}
```

A EmptyKeyError signifies that the request does not contain enough information
to create a key.

#### func (EmptyKeyError) Error

```go
func (eke EmptyKeyError) Error() string
```

#### type LimitKey

```go
type LimitKey interface {
	Key(common.Request) (string, error)
	Type() string
}
```

A LimitKey returns a string key based on the request for creating bucketnames.