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

### Reading Mails in Mac Terminal

Open Mailbox
```
mail
```

To view the first mail
```
t
```

To select the **n**th mail
```
n (integer)
```

To view the next part of the mail
```
spacebar
```

To abort viewing the message
```
q
```

To view the next message in the queue
```
n
```
