# Manu Games, Marketing Assets

Public downloads and shared assets for [The Assembly Line](https://blog.manugames.com)
newsletter and [Tideward](https://tideward.app), our flagship idle RPG for Apple devices.

## What's in here

- **Lead magnet PDFs**, the Factory Game Starter Guide (15 pages), the Factory
  Optimization Checklist (1 page), and the Idle RPG Starter Guide (9 pages). All
  delivered to subscribers via the newsletter.
  These PDFs are **derived artifacts**, built by scripts in our private newsletter
  repo (`build_lead_magnets/*.py`). Never hand-edit one here: rebuild it upstream
  and copy the new file over, or the next rebuild silently reverts the change.
- **`tideward-testflight-qr.png`**, the TestFlight join QR card embedded in the
  welcome email. Also a derived artifact (`build_testflight_qr.py`); it encodes the
  public TestFlight join link.
- **Press kit**: not here. It lives at [manugames.com/press](https://manugames.com/press),
  which is where key art, screenshots and logos are published ahead of the
  2027-02-11 Tideward launch.
- **`docs/research/`**, deep-research reference files supporting the press kit
  and asset decisions. See [`docs/research/INDEX.md`](docs/research/INDEX.md).
  Note: this folder is public; we keep it limited to industry-source-cited
  reference material with no Tideward secrets.

## Direct download links

- [Factory Game Starter Guide (PDF)](https://raw.githubusercontent.com/Manu-Team/manu-marketing/main/factory-game-starter-guide.pdf)
- [Factory Optimization Checklist (PDF)](https://raw.githubusercontent.com/Manu-Team/manu-marketing/main/factory-optimization-checklist.pdf)
- [Idle RPG Starter Guide (PDF)](https://raw.githubusercontent.com/Manu-Team/manu-marketing/main/idle-rpg-starter-guide.pdf)

## Not in here

The newsletter source files, research library, and Tideward development assets
live in a separate private repo. This repo is only the public-facing stuff.

## Maintained by

Manu Games LLC · [@Sethmr](https://github.com/Sethmr)
