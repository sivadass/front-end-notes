# Images

### Fallback iamge when src URL becomes 404
```
<img src="../somepath/image.png" onError={(e)=>{e.target.src=DEFAULT_IMG}}//>
```
