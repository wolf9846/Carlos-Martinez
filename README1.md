# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          template: classic
          base: header, activity, community, repositories, metadata
          config_octicon: yes
          config_timezone: America/Mexico_City
          plugin_achievements: yes
          plugin_achievements_display: detailed
          plugin_achievements_secrets: yes
          plugin_achievements_threshold: C
          plugin_anilist: yes
          plugin_anilist_limit: 2
          plugin_anilist_limit_characters: 22
          plugin_anilist_medias: anime, manga
          plugin_anilist_sections: favorites
          plugin_anilist_shuffle: yes
          plugin_anilist_user: .user.login
          plugin_followup: yes
          plugin_followup_archived: yes
          plugin_followup_sections: repositories
          plugin_languages: yes
          plugin_languages_analysis_timeout: 15
          plugin_languages_analysis_timeout_repositories: 7.5
          plugin_languages_categories: markup, programming
          plugin_languages_colors: github
          plugin_languages_limit: 8
          plugin_languages_recent_categories: markup, programming
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%
          plugin_leetcode: yes
          plugin_leetcode_limit_recent: 2
          plugin_leetcode_limit_skills: 10
          plugin_leetcode_sections: solved
          plugin_leetcode_user:  C4lup0Sec
          plugin_topics: yes
          plugin_topics_limit: 15
          plugin_topics_mode: icons
          plugin_topics_sort: random