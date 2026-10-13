# MealsOn — Health delivered in a box

A responsive, working front-end portfolio prototype based on Divya's MealsOn Figma screens and the Group 7 MIS 6308 systems-analysis design. This implementation is separate from the existing Lovable project.

## Run locally

Requires Python 3 and a modern browser. Node.js 18+ is needed only for the unit tests. No dependency installation or API keys are required.

```bash
python3 -m http.server 8000 --directory dist
```

Open http://localhost:8000. Choose **Explore the demo**. Stop the server with Ctrl+C.

```bash
npm test
```

## Working features

- Responsive meal catalog, live search, dietary filters and meal details.
- Favorites, cart quantities, integer-cent totals and simulated checkout.
- Order history, cancellation and step-by-step simulated delivery tracking.
- Nutrition journal, real totals from demo logs, seven-day chart and water tracking.
- Challenges, membership and daily check-ins.
- Editable preferences, mock wearable consent with blocked sync after revocation.
- Local data export and reset, profile-separated demo storage and event log.
- Local image preview with explicitly simulated meal-scanner results.

Ordering is deliberately separate from logging a meal as eaten. Nutrition values are fictional sample estimates.

## Demo walkthrough

1. Enter Alex's demo profile; search for a meal and save a favorite.
2. Add two meals; open the cart icon; use a fictional delivery address.
3. Place the demo order; track it; advance through delivery states.
4. Log a meal as eaten; view Nutrition from desktop navigation (on mobile, access through Home's View nutrition link).
5. Join a challenge from Home; check in.
6. In Profile, try sync before consent, grant consent, sync, revoke, then try again. View the local event log.
7. Switch to Sam using the profile selector to demonstrate independent local demo data.

## Architecture

`index.html` loads `app.js` and `model.js`; `styles.css` defines responsive presentation. State is serialized into localStorage under a per-demo-profile key. The active demo profile is held in sessionStorage. Unit tests exercise cart, checkout, delivery/cancellation state transitions, and nutrition totals.

## Important limitations

This is a front-end MVP prototype, not a production service or a completed security lab. Local profile selection is NOT authentication. Browser storage and the local event log can be read or edited by the user. There is no server-side ownership enforcement, real payment, actual delivery, AI model, provider integration, password handling, or multi-device synchronization. Use fictional information only.

## Attribution

Original MealsOn mobile screen designs: Divya. Original system design: Group 7, MIS 6308 (John Jiang, Hongzhi Liu, Maksym Lysun, Divya Makanaboina, Jorge Rodriguez). This repository contains a new portfolio implementation inspired by those designs; it does not contain or alter the Lovable source. Uploaded group documents are not redistributed. Confirm group permissions before adding original diagrams or the assignment PDF publicly.

Food pictograms are operating-system emoji, not exported Figma assets. Design fidelity can be improved with original logo, fonts and food-image assets.

## GitHub publication

Create an empty `mealson-mvp` repository on GitHub, without initializing it with files. Authenticate using GitHub Desktop or your supported Git credential method. From the extracted project folder:

```bash
git init -b main
git add dist tests docs package.json README.md .gitignore
git diff --cached
git commit -m "Add MealsOn interactive portfolio prototype"
git remote add origin https://github.com/YOUR_USERNAME/mealson-mvp.git
git push -u origin main
```

Replace YOUR_USERNAME. Review staged files before committing. Pin the repository on your profile. For GitHub Pages, deploy the contents of `dist` with your chosen Pages workflow; the app uses relative asset links. The source download intentionally excludes private Sites metadata and Git history.

## Next phase

See `docs/SECURITY-ROADMAP.md` for real identity, order ownership, consent enforcement, audit logging and test plans. See `docs/ACCEPTANCE.md` for implemented behavior and verification limits.
