### Hi there, I'm Marco 👋


[![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=Mmark94&show_icons=true&theme=radical)](https://github.com/anuraghazra/github-readme-stats)

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Mmark94)](https://github.com/anuraghazra/github-readme-stats)

<p align="center"> 
  Visitor count<br>
  <img src="https://profile-counter.glitch.me/sagar-viradiya/count.svg" />
</p>


// This app initially started from Flavio Copes analytics example
// but diverged quite a bit to generate images as well as track views
// https://flaviocopes.com/count-visits-static-site/

const express = require('express')
const app = express()

// no db - so global var to keep track of count
let counter = 0

function getCountImage(count) {
  // This is not the greatest way for generating an SVG but it'll do for now
  const countArray = count.toString().padStart(6, '0').split('');

  const parts = countArray.reduce((acc, next, index) => `
        ${acc}
        <rect id="Rectangle" fill="#000000" x="${index * 32}" y="0.5" width="29" height="29"></rect>
        <text id="0" font-family="Courier" font-size="24" font-weight="normal" fill="#00FF13">
            <tspan x="${index * 32 + 7}" y="22">${next}</tspan>
        </text>
`, '');
  
  return `<?xml version="1.0" encoding="UTF-8"?>
<svg width="189px" height="30px" viewBox="0 0 189 30" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <title>Count</title>
    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
      ${parts}
    </g>
</svg>
`
}

// get the image
app.get('/count.svg', (req, res) => {
  counter++;
  
  // This helps with GitHub's image cache 
  //   see more: https://rushter.com/counter.svg
  res.set({
  'content-type': 'image/svg+xml',
  'cache-control': 'max-age=0, no-cache, no-store, must-revalidate'
  })
  
  // Send the generated SVG as the result
  res.send(getCountImage(counter));
})

const listener = app.listen(process.env.PORT, () => {
  console.log('Your app is listening on port ' + listener.address().port)
})

<!--
Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
