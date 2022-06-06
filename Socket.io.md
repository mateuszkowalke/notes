# Socket.io

### Proxying client in react app
The client can't actually be proxied, even though the react proxy settings are correct. The problem is client's object contains remote host data itself. It would have to be set through client directly which is not ideal solution.