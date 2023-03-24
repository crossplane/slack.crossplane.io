# slack.crossplane.io

This repo contains a very simple landing page for Crossplane Slack workspace
invitations. When visitors browse to https://slack.crossplane.io, they come to
this page, which simply contains a static HTML page that redirects them to an
official Slack invitation link.

Ideally, we could point `slack.crossplane.io` directly to the invitation, but
DNS does not allow you to do that because the invite link has a full URL path
that contains payload data.  Therefore, we have this very simple HTML page to
perform the redirect for us.

## Maintenance Notes

This repository will need some ongoing maintenance to continue functioning.  We
will be exploring a better long term solution, but for now this repo will serve
our needs for self-service joining of our Slack workspace.

Notes on maintaining this repo can be found below:

* The invitation link that [`index.html`](index.html) redirects to is set to
  never expire time wise, but it will expire after 400 people have used it to
  join the Slack workspace.
  * Therefore, it will need to be regenerated over time.  @jbw976 will take care
    of this on a periodic basis, using the Slack invitation link
    [documentation](https://slack.com/help/articles/201330256-Invite-new-members-to-your-workspace#share-an-invitation-link).
  * When generating a new link, "Never expires" should be selected in the edit
    link settings.
  * Open a PR that updates [`index.html`](index.html) with the new link, then
    ensure the updated link is deployed successfully to the live site.
