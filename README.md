# HydroImaging

Website for the **HydroImaging** workshop series — *Mining Imaging Data for Hydrological and Environmental Modelling*.

**Live site: [hydroimaging.github.io](https://hydroimaging.github.io/)**

The current edition is a satellite workshop of [IEEE ICIP 2026](https://2026.ieeeicip.org/), held on **17 September 2026, 09:00–16:30 EEST**, in room C8 at Tampere University, Tampere, Finland. The programme is a full day of 14 accepted papers across two oral sessions, a keynote by Prof. Kevin Tansey (University of Leicester), and a closing panel discussion.

## Key dates

| Milestone | Date |
| --- | --- |
| Paper submission | 20 May 2026 |
| Reviews due | 10 June 2026 |
| Rebuttal period | 11–15 June 2026 |
| Acceptance notification | 17 June 2026 |
| Final manuscript | 1 July 2026 |
| Author registration | 8 July 2026 |
| Workshop | 17 September 2026 |

All deadlines are at 23:59 AoE (Anywhere on Earth). Submissions go through the ICIP 2026 system at [icip2026.exordo.com](https://icip2026.exordo.com/).

## Organizers

| | |
| --- | --- |
| Mourad Oussalah | University of Oulu, Finland |
| Olof Mogren | RISE Research Institute of Sweden |
| Jukka Heikkonen | University of Turku, Finland |
| Getnet Demil | University of Oulu, Finland |
| Farhan Humayun | University of Turku, Finland |

Supported by the [Digital Water Flagship](https://digitalwaters.fi/) and [Climate AI Nordics](https://climateainordics.com/).

## About this repository

A single-page static site with **no build step, no dependencies and no test suite**: `index.html` holds the markup, all CSS and all JavaScript, alongside an `assets/` directory of images. The only things loaded from elsewhere are Google Fonts, Font Awesome, and — on demand, when a visitor asks for the programme PDF — the jsPDF library.

### Running it locally

Open `index.html` in a browser, or serve the directory so relative paths behave exactly as they do in production:

```bash
python3 -m http.server 8000
```

### Deployment

GitHub Pages serves this repository from its root, so **whatever lands on `main` is live immediately** — there is no CI, no build and no staging environment in between.

Because of that, changes go through a pull request rather than straight to `main`:

1. branch off `main` and commit there,
2. push the branch and open a PR,
3. merge once reviewed,
4. delete the branch **after** the merged result has been checked on the live site — not before, so there is an easy way back if something looks wrong in public.

## Editing the site

A few places couple to each other and are easy to get wrong:

- **Deadlines live in two places.** Each card in the *Important Dates* section shows human-readable text *and* drives a small countdown whose target timestamp is set in JavaScript. Changing a date means changing both.
- **Navigation appears three times** — the desktop bar, the mobile menu and the footer's quick links. All three need the same edit.
- **Speakers and organizers** are a card plus a matching modal that share one identifier. Adding a person means adding both, plus a portrait in `assets/`.
- **The schedule** is a timeline of items, with each oral session drawn as a frame enclosing the papers that belong to it. The papers sit inside the session container, and the "N papers" badge on each session header is counted from that container at load, so it never needs updating by hand.
- **The programme PDF** is generated in the browser from the schedule section itself — there is no PDF file in the repository to keep in sync. Adding a timeline item is enough, as long as it keeps the classes the generator reads for the presenter, room and author list.
- **Both colour themes must work.** Colours come from CSS custom properties defined once for dark and once for light; the theme toggle stores the choice in `localStorage`. Prefer a variable over a literal colour value.

## License

The workshop content, logos and photographs belong to their respective owners and are not covered by an open-source license.
