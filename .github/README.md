# Mastodon fork for [est.social](https://est.social/)

Forked from [Mastodon](https://github.com/mastodon/mastodon/).

This is mainly to increase character limit and to manage localization ahead of the official releases.

## Changes made

Up the char limit to 10,000:

- [compose_form_container.js](app/javascript/mastodon/features/compose/containers/compose_form_container.js)
- [instance_serializer.rb](app/serializers/rest/instance_serializer.rb)
- [v1/instance_serializer.rb](app/serializers/rest/v1/instance_serializer.rb)
- [status_length_validator.rb](app/validators/status_length_validator.rb)

Increase the feed item count to 10,000:

- [feed_manager.rb](app/lib/feed_manager.rb)

## Releases

Releases are tagged with the upstream version plus `-est`, e.g. `v4.7.3-est`.
Pushing a `*-est*` tag builds the `ghcr.io/est-social/mastodon` and `mastodon-streaming` images.

Updating to a new upstream release:

```sh
git fetch upstream --tags
git switch -c update-to-v4.7.4 main
git merge v4.7.4
git push -u origin update-to-v4.7.4
```

Open a PR, merge it, then create a release on GitHub with a new tag `v4.7.4-est` on `main`,
titled "Update to v4.7.4".

Security fixes that can't wait for an upstream release (e.g. a Ruby, Node or gem bump) get a patch
release on top: `v4.7.3-est.1`, `v4.7.3-est.2` and so on, starting again with each upstream version.
For gem fixes, prefer cherry-picking the upstream commit, if there is one, so the next upstream
merge stays clean. Upstream only bumps Ruby and Node on `main`, not on stable branches, so do those
ourselves (`.ruby-version`, `.nvmrc`, `Dockerfile`, `Gemfile.lock`).
The release notes should say what changed and what the server needs (e.g. `rbenv install`,
`bundle install`, restart; whether there are migrations or assets to build).

To rebuild the images of an existing release with updated base images, run the
"Build container release images (fork)" workflow manually and pick the release tag.
