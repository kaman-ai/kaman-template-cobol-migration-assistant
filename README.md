# COBOL Migration Assistant

The app of the **COBOL Migration Assistant** template in the Kaman marketplace, built the way
every app on Kaman is (the reference is the Smart Site Planning desk;
Kai's *Building an app on Kaman* skill teaches it).

Migrates a COBOL program to a modern language the safe way: inventories it and its copybooks, sends constructs like CICS or ALTER to an architect, translates with your migration rules, and proves the result by running old and new code on the same data - a pull request opens only when the outputs match. Upload your migration rules and connect your source and test environments at install.

It is installed as a code project of yours when you install the template.

## What it does

| screen | what it is |
|---|---|
| `/login`, `/signup` | the app's **own** sign-in — its users never see Kaman |
| `/` — the desk | a Kaman **scenario**: the live records from your connected system, read as you, with **Ask** on each |
| `/chat` | Kaman's chat component with the template's agent, as you |
| the header's **Run** | an **action** the desk declares: starts the template's workflow, approvals included |

## How it is wired

- The app **acts as its signed-in user**: every call carries their token
  (`auth.session`), so Kaman applies their permissions and organisation.
  The API key is used only to sign a new person up.
- Kaman's browser components reach Kaman through `app/api/kaman/[...path]`
  (`auth.proxy`), narrowed to the scenario routes. The browser never holds
  a token.
- `kaman.app.json` names the agents, workflow and desk scenario by the ids
  the template seeds them under. **Install rewrites them** to your copies
  and shares exactly those with your organisation.

## Publishing a new version

Push here, then republish the template pinned to the new commit. Installs
always take the pinned commit, never the tip of `main`.
