# Collection Method

Updated: April 15, 2026

## Tools Used
- `yt-dlp 2026.03.03` for YouTube metadata and caption extraction.
- Public LinkedIn post URLs for manual post collection.
- Markdown files for normalized notes, dates, links, summaries, and key insights.

## YouTube Metadata Verification Command
```powershell
yt-dlp --skip-download --print "%(id)s | %(title)s | %(upload_date)s | %(duration_string)s | %(channel)s" <youtube-urls>
```

The command was run against the eight YouTube links listed in the manifest below. Verified metadata:
```text
T9d4GOCpBIE | SEO for LLMs: Adapting to the AI-first Web with Aleyda Solis & Ray Grieselhuber #seo #webinar | 20250522 | 1:00:20 | Sitebulb
BjyF_4UhoOM | The AI Search Optimization Roadmap (Aleyda Solis) | 20250909 | 1:03:54 | Dennis Shiao
hMFrOxAZe6k | High-Intent Content Strategies for AI SEO with Cairrot | 20260316 | 3:09 | Best SEO Podcast: Search with LLM Visibility
oG6qw6T38aQ | Clickstream Data Insights: How AI Reveals Hidden Opportunities | 20260317 | 2:23 | Best SEO Podcast: Search with LLM Visibility
UaK-N7zGq70 | Creating Content Google Can Not Ignore with Bernard Huang | 20221109 | 55:48 | Jaryd Krause - Buying Online Businesses
33OLfnufbXg | #014: How to Build Systems for Content & SEO (+ Advanced Poker Tips) w/ Bernard Huang (Co-founder at Clearscope) | 20240408 | 1:22:20 | Omniscient
YDqpxuGkfhw | SEOs Who Ignore Distribution Will Fall Behind - Ross Simmonds - Inside SEO Week | 20260210 | 15:57 | iPullRank
xLWBDKX-_3Q | How to Rank #1 When AI Is Taking Over ft. Ross Simmonds | 20241203 | 39:52 | Marketing Against the Grain
```

## YouTube Caption Extraction Command
```powershell
yt-dlp --write-auto-subs --sub-langs en-orig,en --sub-format vtt --skip-download -o "research/youtube-transcripts/raw/%(id)s.%(ext)s" <youtube-urls>
```

For the Ross Simmonds Marketing Against the Grain video, YouTube exposed `en-US` captions instead of `en`/`en-orig`, so this command was used:

```powershell
yt-dlp --write-subs --write-auto-subs --sub-langs en-US --sub-format vtt --skip-download -o "research/youtube-transcripts/raw/%(id)s.%(ext)s" https://www.youtube.com/watch?v=xLWBDKX-_3Q
```

## YouTube Manifest

| Expert | Video ID | Link | Upload date | Raw caption files |
| --- | --- | --- | --- | --- |
| Aleyda Solis | `T9d4GOCpBIE` | https://www.youtube.com/watch?v=T9d4GOCpBIE | May 22, 2025 | `T9d4GOCpBIE.en-orig.vtt`, `T9d4GOCpBIE.en.vtt` |
| Aleyda Solis | `BjyF_4UhoOM` | https://www.youtube.com/watch?v=BjyF_4UhoOM | September 9, 2025 | `BjyF_4UhoOM.en-orig.vtt`, `BjyF_4UhoOM.en.vtt` |
| Connor Kimball | `hMFrOxAZe6k` | https://www.youtube.com/watch?v=hMFrOxAZe6k | March 16, 2026 | `hMFrOxAZe6k.en-orig.vtt`, `hMFrOxAZe6k.en.vtt` |
| Connor Kimball | `oG6qw6T38aQ` | https://www.youtube.com/watch?v=oG6qw6T38aQ | March 17, 2026 | `oG6qw6T38aQ.en-orig.vtt`, `oG6qw6T38aQ.en.vtt` |
| Bernard Huang | `UaK-N7zGq70` | https://www.youtube.com/watch?v=UaK-N7zGq70 | November 9, 2022 | `UaK-N7zGq70.en-orig.vtt`, `UaK-N7zGq70.en.vtt` |
| Bernard Huang | `33OLfnufbXg` | https://www.youtube.com/watch?v=33OLfnufbXg | April 8, 2024 | `33OLfnufbXg.en-orig.vtt`, `33OLfnufbXg.en.vtt` |
| Ross Simmonds | `YDqpxuGkfhw` | https://www.youtube.com/watch?v=YDqpxuGkfhw | February 10, 2026 | `YDqpxuGkfhw.en-orig.vtt`, `YDqpxuGkfhw.en.vtt` |
| Ross Simmonds | `xLWBDKX-_3Q` | https://www.youtube.com/watch?v=xLWBDKX-_3Q | December 3, 2024 | `xLWBDKX-_3Q.en-US.vtt` |

## LinkedIn Collection Notes
- LinkedIn posts are organized by author in `research/linkedin-posts/`.
- Each post note includes a direct URL, date, summary, and key insights.
- Public LinkedIn pages can show relative dates to logged-out viewers, so absolute dates were captured in the research notes where the post or source context made them available.
- LinkedIn activity IDs were also decoded as a sanity check for approximate post dates when pages exposed only relative dates.

## Accuracy Notes
- YouTube dates in the transcript notes use the verified upload date returned by `yt-dlp`.
- Raw caption files are YouTube caption artifacts and may include auto-caption quirks.
- The author-level transcript markdown files keep the research usable by summarizing the high-signal points from the raw captions instead of forcing readers to inspect long VTT files.
