# Screen Picks

A shared list where a group of friends recommend movies and TV shows, mark what they've watched, and give each pick a verdict.

It is a single page (`index.html`) published as a claude.ai artifact. It uses the artifact runtime for its shared database and to know who is viewing, so it only works when opened as that artifact on claude.ai. Opening the file directly in a browser shows the page shell with a notice instead of the list.

## Features

- **Two tabs:** *The list* and *Add a pick*
- **Picks:** movie or TV show, title, year, up to 3 genres (each with an icon), where to watch (Prime Video, Netflix, JioHotstar, Apple TV or elsewhere) and a one-line note
- **Verdicts:** 👑 Perfection (*Gaand phaad*), 👍 Go for it (*Dekh le*), Time pass (*Paise uda k kya krega mujhe dede*), 💩 Skip it (*Ganja Phook k dekhega toh aacha lagega*)
- **Group verdict:** the most-voted verdict for each pick; ties go to the one closest to the group's average
- **Filters:** seen / not seen for any member, movies / shows, genre, newest / top rated, and text search
- **Editing:** whoever added a pick can edit or remove it
- **Joining:** new people join with a one-time invite code. A member asks the group to add someone, every other member has to approve, and one rejection ends the request. Each member can invite at most 2 people per calendar month.

## Data

Stored in the artifact's database:

| Collection | What it holds |
|---|---|
| `movies` | the picks |
| `marks` | each member's name, membership and their watched / verdict map |
| `proposals` | invite requests and votes |
| `invites` | SHA-256 hashes of invite codes (the codes themselves are never stored here) |
| `data/users/<id>` | each proposer's own invite codes, private to them |

The voting and invite limit are enforced by the page, not by the database, so they work on trust within the group. Who can open the page at all is controlled from the artifact's Share menu on claude.ai.
