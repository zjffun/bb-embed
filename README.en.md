# bilibili embed image overlay

A tool to add more visual cue when embedding bilibili videos in GitHub.

## Run app localy

- Make sure to have [nix package manager](https://nixos.org/download.html) installed.
- Clone repo & cd into it.
- Run: `nix-shell`
- Inside the shell run `gunicorn -w 4 -b 0.0.0.0:8080 wsgi:app` and visit http://localhost:8080/

## Example

## Deployment & Hosting

I used [heorku](https://heroku.com/) for deployment. The app is hosted on https://yt-embed.herokuapp.com/
