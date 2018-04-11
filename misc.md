# Miscellaneous

### Random Color Generator
```
function getRandomColor() {
  let letters = '0123456789ABCDEF'
  let color = '#'
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)]
  }
  return color;
}
```

### Updating VS Code in Ubuntu
```
sudo dpkg -r code
sudo dpkg -i code_downloaded_package.deb
```
