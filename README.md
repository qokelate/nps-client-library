# NPS-client-c-library

### from `https://github.com/ehang-io/nps`

### `x86_64` only

### example

```
#ifndef GO_CGO_PROLOGUE_H
#define GO_CGO_PROLOGUE_H

typedef long long GoInt64;
typedef GoInt64 GoInt;
#endif

#ifndef GO_CGO_GOSTRING_TYPEDEF
typedef struct { const char *p; ptrdiff_t n; } _GoString_;
#endif

#ifndef GO_CGO_GOSTRING_TYPEDEF
typedef _GoString_ GoString;

#endif

extern "C"
{
//StartClientByVerifyKey(serverAddr, verifyKey, connType, proxyUrl)
void ClientStart(GoString p0, GoString p1, GoString p2, GoString p3, GoInt timeout_sec);
int64_t StartClientByVerifyKey(const char *p0, const char *p1, const char *p2, const char *p3);
}

GoString pack_GoString(const std::string& string1)
{
    GoString a = {0};
    a.p = string1.c_str();
    a.n = string1.length();
    return a;
}


...


ClientStart(pack_GoString("xxx:xxx"), pack_GoString("xxx"), pack_GoString("tcp"), pack_GoString(""), 30);
```