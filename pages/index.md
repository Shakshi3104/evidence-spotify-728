---
title: Spotify Naniwa Danshi
---

<Details title='What is this?'>

  このダッシュボードは、Spotify Web APIで取得できるデータを、[dlt](https://dlthub.com/)と[dbt](https://docs.getdbt.com)を使ってELTしたものを可視化しています。
</Details>

## Summary

```sql songs_summary
select
  count(track_title) as song_count
from spotify_naniwa_danshi.tracks
```

```sql avg_popularity
select
  avg(popularity) as avg_popularity
from spotify_naniwa_danshi.tracks
```

<BigValue
  data={songs_summary}
  value=song_count
  title="Songs"
/>

<BigValue
  data={avg_popularity}
  value=avg_popularity
  title="Avg Popularity"
/>

## Top Tracks

```sql top_tracks
select
  track_title,
  popularity
from spotify_naniwa_danshi.tracks
order by popularity desc
limit 20
```

<BarChart
  data={top_tracks}
  x=track_title
  y=popularity
  swapXY=true
/>

## Details

```sql all_tracks
select
  *
from spotify_naniwa_danshi.tracks
order by release_date
```

<DataTable data={all_tracks} 
  rows=all search=true>
</DataTable>