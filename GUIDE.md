## Tags are images

The basic system used to make twine a Japanese VNovel style engine is the tags

Here we have the top of a story 'section'

`:: Academy [bg-school player ltalk npc-school] {"position":"1575,625","size":"200,100"}`

It's divided into a few parts:

- Academy -> is the name of the story section
- [...] -> These are the **tags**, `bg-*` is used to denote which background the section has, the `player` tag denotes the player should be visible, the `ltalk` highlights the player to mark them as speaking, and `npc-school` denotes the other person that is visible.
- `{"position":"1575,625","size":"200,100"}` is a coordinate used by the Twee 3 tools so you can show a see a twine-like visual map of the story (See README)

### Adding BG Images

within the `story/styles` folder there are a number of files that are called `stylesheet.**.twee`, these are CSS stylesheets, the two main ones for images are

`stylesheet.char.twee`
`stylesheet.bg.twee`

Taking a look into the **.bg.** file we can see some entries:

```
body[data-tags~="bg-city"] {
  background-image: url("./media/images/bg/city.webp");
}
```

This the base for a background we want to follow

`body[data-tags~="bg-city"]`

`body` targets the body element, where we want to place all our background images

`[data-tags~="bg-city"]` says when current twine section has the tag **bg-city** apply this background.

For any new entries, we just need to replicate this, then changing the 
`background-image: url("./media/images/bg/city.webp");` to point to the location of the new background within the `media/images/bg` folder (this folder structure is an example, you can choose your own).

Then give it a memorable tag name, eg;

```
body[data-tags~="bg-new"] {
  background-image: url("./media/images/bg/new.webp");
}
```

### Adding a new character image

Character images follow a similar process to a background, except for the top section

`body[data-tags~="npc-gym"] .img3 { ... }`

For characters, you'll notice after the [] for the tags a `.img3` or `.img1`, these correspond to the images location

1 = left   2 = middle  3 = right

So if you prefer the player to be always on the left, all player variations (anrgy, sad, etc, should follow the same format but just use a tag that denotes the expression/situation/outfit) should end with .img1.


### Special tags

`mid-char` this tag widens the center image if only one character is to appear in the middle of the page and wants to be given prominence.

`trio-char` If three characters are present, this tag gives equal space.

### Additional Notes

If web hosting, use .webp it has transparency like .png, but uses much less space photopea.com can be very helpful here (web based photoshop-lite)

Use the same aspect ratio for character portraits, otherwise you may find their size will change, as the styling will try to maximise the size of the image (this is to insure good presentation on larger screens)