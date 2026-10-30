# SBD ScanTrack - Project Data Explorer

A Trimble Connect project extension that reads project data through the Trimble Connect Core REST API (`/tc/api/2.0`).

## Files

| File | Purpose |
|---|---|
| `index.html` | The application (single file, no build step) |
| `manifest.json` | Extension manifest read by Trimble Connect |
| `image.svg` | Extension icon |
| `readme.md` | This document |

## Features

- Automatic access-token request through the Workspace API (`extension.requestPermission`), with a manual token option for standalone use
- Project list and current-project detection, with regional API address lookup (`/regions`)
- Tabs: Files & Folders (folder navigation, download links), ToDos (create, edit, delete), Team Members, Saved Views
- Row filter and CSV export on every tab
- Custom REST request tool (GET, POST, PUT, DELETE)
- Request log with HTTP status and timing

## REST endpoints used (base: `/tc/api/2.0`)

`GET /regions`, `GET /projects`, `GET /folders/{id}/items`, `GET /todos?projectId=`, `GET /projects/{id}/users`, `GET /views?projectId=`, `GET /files/fs/{id}/downloadurl`, `POST /todos`, `PUT /todos/{id}`, `DELETE /todos/{id}`

Some response fields may differ by Connect version. Use the Custom REST Request tool and the Request Log to confirm.

## Deployment (GitHub Pages)

1. Create a new **public** repository named `SBD_REST`.
2. Upload all four files to the repository root.
3. In **Settings > Pages**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. Open `https://majeedjawhar-gif.github.io/SBD_REST/index.html` to confirm it loads.
5. If you use a different username or repository name, update `url` and `icon` in `manifest.json`.

## Installation in Trimble Connect

1. Open a project as a project administrator.
2. Go to **Project Settings > Apps & Capabilities > Add Custom**.
3. Enter `https://majeedjawhar-gif.github.io/SBD_REST/manifest.json`.
4. Enable the extension, open it from the project's left navigation, and approve the access-token consent prompt.

If you change the manifest later, remove the extension and add it again, because Connect stores the manifest contents when it is added.

## Notes

- The token grants only what the signed-in user can already access. All built-in actions are read-only.
- If requests fail before any HTTP status appears in the log, check the browser console for CORS errors.
