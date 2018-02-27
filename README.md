# Front-end Notes

### Reduce file size when saving image from canvas using `toDataUrl` method

```
var fullQuality = canvas.toDataURL('image/jpeg', 1.0);  
var mediumQuality = canvas.toDataURL('image/jpeg', 0.5);   
var lowQuality = canvas.toDataURL('image/jpeg', 0.1);
```
