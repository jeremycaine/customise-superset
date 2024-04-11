# Change fonts in Superset

## 1. Add IBM Plex Font to app
In `superset-frontend` 
- add a `fonts` folder under `src/assets/stylesheets/less`
- add the CSS and WOFF2 files in this repo to the folder.

## 2. Link to IBM Plex font stylesheets
Delete references to other fonts that Superset came with and link in IBM Plex fonts

`src/assets/stylesheets/less/fonts.less`
```
// in `fonts` there are all the IBM Plex WOFF2 files and a number of CSS
// dependeing on which Plex fonts (incl Thin, Bold, Italic etc) - add their CSS file here
@import './fonts/IBMPlexMono-Regular.css';
@import './fonts/IBMPlexSans-Regular.css';
@import './fonts/IBMPlexSerif-Regular.css';
```

## 3. Update the font variables
`src/assets/stylesheets/less/variables.less`
```
@font-family-sans-serif: 'IBM Plex Sans', 'Helvetica Neue', Arial, sans-serif;
@font-family-serif: 'IBM Plex Serif', 'Georgia', Times, serif;
@font-family-monospace: 'IBM Plex Mono', 'Menlo', 'DejaVu Sans Mono',
'Bitstream Vera Sans Mono', Courier, monospace;
@font-family-base: @font-family-sans-serif;
```

## 4. Update Superset UI
Update `superset-frontend/packages/superset-ui-core/src/style/index.tsx`
```
  typography: {
    families: {
      sansSerif: `'IBM Plex Sans', 'Helvetica Neue', Arial, sans-serif`,
      serif: `'IBM Plex Serif', 'Georgia', Times, serif`,
      monospace: `'IBM Plex Mono', 'Menlo', 'DejaVu Sans Mono',
      'Bitstream Vera Sans Mono', Courier, monospace`,
    },
  ...
```

If running `superset` locally outisde of Docker you can then do 
- `npm run build` in `superset-frontend`
- restart superset with `superset run -p 8088 --with-threads --reload --debugger'



