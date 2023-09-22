# Mastodon fork for [est.social](https://est.social/)

Forked from [Mastodon](https://github.com/mastodon/mastodon/).

This is mainly to manage localization ahead of the official releases.

## Changes made

1. Upped char limit to 10,000 after some [discussion](https://est.social/@diana/109989076059242012) on our site.
   - app/javascript/mastodon/features/compose/components/compose_form.jsx
   - app/javascript/mastodon/features/compose/components/character_counter.jsx
   - app/serializers/rest/instance_serializer.rb
   - app/serializers/rest/v1/instance_serializer.rb
   - app/validators/status_length_validator.rb
2. Localization. These come from the official [Crowdin project](https://crowdin.com/project/mastodon/et) but they are merged ahead of the official releases.
   - app/javascript/mastodon/locales/et.json
   - config/locales/activerecord.et.yml
   - config/locales/devise.et.yml
   - config/locales/doorkeeper.et.yml
   - config/locales/et.yml
   - config/locales/simple_form.et.yml
