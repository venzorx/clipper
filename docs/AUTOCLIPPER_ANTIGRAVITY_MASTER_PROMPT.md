# AUTOCLIPPER PRO — ANTIGRAVITY MASTER PRODUCTION BUILD PROMPT

Repository: https://github.com/venzorx/clipper.git
Target: Windows 11 x64 desktop application
Baseline: the 24-page AutoClipper Pro Product & Engineering Blueprint (v1.0, 16 Nov 2026) plus the additions in this prompt.

## 0. Mission

Act as lead desktop architect, Python/media engineer, AI integration engineer, Windows release engineer, QA lead, security reviewer and technical writer. The GitHub repository is newly created and initially empty except its README. Inspect it before changing anything.

Build a real installable Windows desktop application, not a website-only prototype, static mockup or disconnected scripts. Use a React + TypeScript + Tauri desktop UI, Python local processing service, SQLite persistence, FFmpeg/ffprobe media engine and local AI adapters. Implement in phases, run tests and builds, fix failures, and continue until acceptance criteria pass or a genuine external blocker is documented. Maintain IMPLEMENTATION_STATUS.md with truthful implemented/tested/partial/blocked/not-implemented states.

Product promise: one creator-authorized source in; a complete short-form content package out. The operator should not need to manually transcribe, identify moments, write scripts, record narration, edit a timeline, create captions, design covers, write metadata or assemble folders. Operator remains responsible for valid rights, credentials, final review and publishing.

Target up to 3 strong clips per day (1,095 target clips/year). This is a target, not a quota. Never manufacture weak clips to meet a count. Return fewer if fewer strong moments exist.

## 1. Non-negotiable rules

- Windows-first desktop application with installer and desktop shortcut.
- Local-first media/AI pipeline; no mandatory recurring inference API bill for core functionality.
- English-only generated narration in v1.
- Multiple built-in English narrator voices; adaptive voice selection and consistent-channel-voice option.
- No voice cloning or streamer voice imitation.
- No unauthorized scraping, cookie/session extraction, DRM circumvention, hidden endpoints, download bypass or anti-bot evasion.
- Public URL does not equal permission. Credit is not permission.
- Missing, expired or out-of-scope permission means BLOCKED for publish-ready export.
- AI voiceover alone is not meaningful original value. Commentary adds a specific explanation, context, critique, analysis or distinct viewer takeaway.
- No editing tricks to evade Content ID or platform enforcement.
- No fake engagement, automated likes, comment spam, engagement exchanges or mass repetitive publishing.
- Never promise viral views, reach, no copyright claims, no strikes, no YPP approval or no shadowban.
- Never fabricate events, reactions, quotes, outcomes, visual evidence or factual claims.
- No public upload or visibility change without owner authorization and explicit confirmation. Export-only by default.
- Never commit secrets, tokens, model weights, private media, caches or exports.
- Every job is observable, safely cancellable, resumable and diagnosable.
- Never label partial, unreviewed or rights-uncertain work upload-ready.

## 2. Repository layout

Create a maintainable monorepo:
- apps/desktop: Tauri + React + TypeScript
- services/engine: Python worker/service
- packages/shared-types: shared schemas/contracts
- config/model-registry: pinned model IDs/revisions/licences/hashes
- config/presets: render, captions, channels
- docs: product, architecture, user, setup, platform, privacy, licence docs
- scripts: PowerShell dev/setup/build/verify
- tests: unit/integration/acceptance fixtures
- .github/workflows: CI
- README.md, IMPLEMENTATION_STATUS.md, CHANGELOG.md, .gitignore, .env.example

Use only original/synthetic/licensed test fixtures. Do not add large weights or creator recordings to Git.

## 3. Architecture

Desktop: React + TypeScript + Tauri 2.x, dark professional accessible UI. Screens: Dashboard, New Job, Source Library, Rights, Auto Discover, Live Monitor, Candidates, Preview Studio, Voice Studio, Publishing Pack, QA, Export Manager, Settings, Diagnostics.

Local service: Python worker/API bound to loopback only. Handles orchestration, model/media adapters, SQLite, events, retries and filesystem. Validate all paths; prevent traversal; no public network binding.

Storage: migration-managed SQLite. App data under user local application-data directory; media/cache/projects in configurable folders; exports in a user-selected directory. Preserve original sources.

Job state machine:
QUEUED → VALIDATING_SOURCE → RIGHTS_CHECK → INGESTING → AUDIO_ANALYSIS → TRANSCRIBING → SCENE_ANALYSIS → CANDIDATE_DETECTION → RANKING → SCRIPTING → TTS → EDIT_PLANNING → RENDERING → QA → EXPORT_READY.
Alternate states: NEEDS_REVIEW, BLOCKED, FAILED, CANCELLED, PARTIAL_SUCCESS.
Persist transitions/timestamps and intermediate assets. Atomic final rename. Resume after interruption. Never fake progress percentages.

## 4. Free-first local model stack

Treat these as proposed defaults; validate exact revision, licence, dependencies, Windows compatibility and performance before release. Pin revisions/hashes and do not silently upgrade.

- Reasoning/scripts/metadata: Qwen3.5-4B through a local runtime such as Ollama, quantized 4-bit class if available. Use an 8K application context by default. Fallback to Qwen3.5-2B if benchmark on target PC shows 4B is too heavy.
- English transcription: faster-whisper + English Distil-Whisper Small, CPU INT8. Cache by source checksum + model revision + settings. Retry important low-confidence sections with larger English model only if installed and resources permit.
- English TTS: Kokoro-82M local, multiple auditioned built-in English voices. Adaptive mode and consistent channel voice mode. No cloning.
- Visual analysis: OpenCV + limited candidate-directed frame samples + local vision-capable model only if validated.
- Scene detection: PySceneDetect/OpenCV/FFmpeg.
- Editing: FFmpeg + ffprobe.
- Covers: Pillow + SVG.
- Persistence: SQLite.

Use one heavy model at a time on a 16 GB RAM laptop. Do not assume a dedicated GPU. The exact CPU/GPU is unknown until detected. Default local inference has no per-call API bill; electricity, downloads, storage, optional platform API access and internet are separate costs.

Gemini API remains disabled per the baseline age/provider restrictions. Cloud TTS/LLM may only be enabled after confirming operator age, application audience, provider terms, privacy and licence eligibility. Do not bypass terms or upload private creator media/voice data without permission.

Model registry must record provider, exact model ID/revision/hash, quantization, size, task, language, licence URL, notices, compatibility, source URL and review date. Downloads visible, resumable and hash-checked, outside Git.

## 5. First-run and daily user journey

First-run wizard:
- detect Windows, CPU, RAM, GPU/driver/encoders where available, disk space
- choose Low Resource/Balanced/Quality profile
- verify FFmpeg/ffprobe and licence notices
- download models after showing sizes/licences
- set workspace and output folder
- set channel name, niche, brand, English narration and voice mode
- allow voice audition
- explain platform API permissions, quotas, media rights and live-chat limitations
- show diagnostics/model readiness

Daily home screen:
- Create from Local File
- Create from Authorized Source
- Auto Discover
- Live Monitor
- Recent Jobs

Normal local job should require source selection, permission confirmation, platform export selection and Create Shorts Pack. No manual timeline editing should be required.

## 6. Source intake and rights

Supported modes: local file owned/authorized by operator; creator-provided authorized file; official platform metadata discovery; documented permitted media access/authorized handoff; live monitoring only through documented APIs and explicit source permission.

Do not implement arbitrary scraping or unauthorized download. Discovery metadata does not grant media access or publication rights. If API provides metadata but not bytes, clearly ask for an authorized file.

Rights record fields: source asset ID; creator/rightsholder; source URL/delivery reference; permission evidence; allowed platforms; commercial/monetization scope; derivative edit permission; territory/expiry; attribution; music/third-party clearance; reviewer/time.

Statuses:
PASS = evidence covers source, transformations, platform and intended use.
NEEDS_REVIEW = human decision/evidence required; not ready.
BLOCKED = no/expired/contradictory/out-of-scope permission or prohibited access method.

Credit is not permission. Short duration, crop, captions, filters or voiceover are not automatic legal safe harbour.

## 7. Auto Discover and Live Monitor additions

Initial category preset: GTA 6/gaming. Use official supported discovery endpoints only. Display actual available metadata: creator/channel, title, category, platform, public viewer metadata if returned, URL, time checked, access state, permission state. Rank transparently by relevance, live status, returned popularity metadata, freshness, English fit and allowlist. Never invent values.

Discovery is not download permission. Do not acquire protected media without permission and a supported technical route. Respect quotas, rate limits and caching.

Live Monitor only for permitted sources. Chat velocity only where an official supported live-chat API exposes it and scopes allow it. Do not claim historical chat spikes from ended VODs. Unavailable signals must be labelled unavailable, never simulated. Audio signals may include RMS/peak deviation, laughter/speech activity, sudden energy change and transcript context; loudness alone is not a viral score.

Local-file mode must work without platform credentials.

## 8. Audio-first pipeline

For an authorized local video:
1. ffprobe validates integrity, streams, duration, dimensions, codecs and timestamps.
2. Extract compressed analysis audio; preserve source.
3. Run English ASR once and cache.
4. Detect silence, speech activity, audio peaks, clipping and loudness changes.
5. Build scene map via low-rate sampling.
6. Merge transcript, audio events, sampled visual evidence and optional authorized live-chat events into event map.
7. Analyse complete source in sequential context windows of about 12 minutes, with overlap; split further if token limits require.
8. Detect candidates; render only selected timestamp segments when legally and technically available.

Explain correctly: audio-only analysis reduces analysis storage/compute, but does not remove need to possess a local full source video if that is the authorized input.

Candidate data: start/end ms, verified summary, context, event, payoff, transcript excerpt, scene/visual refs, audio risks, why viewer cares, commentary angle, confidence, score breakdown, source segments and rights reference.

Never cut context or payoff misleadingly. Deduplicate overlaps.

## 9. Moment ranking and best-three policy

Use baseline weights:
- context/standalone clarity 25%
- story/payoff 20%
- viewer interest/emotion 15%
- commentary potential 15%
- audio/visual quality 15%
- originality/diversity 10%

These are product heuristics, not YouTube ranking weights or virality predictors.

Detect funny fails, discoveries, first reactions, surprise, explanations, disagreement/hot takes, emotional reactions and payoff. Penalize filler, contextless shouting, hidden backstory, cut-off payoff, poor speech, unsupported claims, private data and duplicates.

Chat velocity only when real authorized signal exists; normalize against that stream's baseline and retain sample/missingness. Do not compare raw counts across channels without normalization.

Generate up to 8 candidates and select up to 3 by quality/diversity. Three is a target/ceiling, not quota. Return fewer if necessary. Explain rejections.

## 10. English script engine — engagement-oriented, truthful

For each selected moment:
1. Understand actual source event from transcript and visual evidence.
2. Generate several hook options: moment-led, curiosity-led, surprise-led, explanation-led.
3. Select strongest truthful hook.
4. Add minimum context for a new viewer.
5. Add a specific original observation/analysis/explanation.
6. Resolve hook with payoff/takeaway.
7. Add CTA only if genuinely relevant.

Do not merely paraphrase the streamer. No generic “watch till the end,” false stakes, fake quotes, fabricated reactions/results or unsupported claims. Label opinion/uncertainty. Match word count to clip duration.

Use strict JSON: hook options, chosen hook, context, analysis, payoff, optional CTA, full script, word count, estimated duration, factual claims, evidence refs, uncertainties, quality scores, rejection reasons, prompt version.

A separate script critic scores first-second relevance, real curiosity/payoff, clarity, context, flow, pace, duration fit, originality, factuality and footage synchronization. Penalize generic/filler/repetitive scripts. Regenerate a bounded number of times, then flag/omit.

## 11. Voice engine

Kokoro-82M local English TTS is proposed primary after exact model/dependency licence and Windows compatibility review. TTS provider adapter should allow future eligible alternatives without rewriting editor. Provide several real built-in English voice IDs, audition panel, adaptive choice by clip category and consistent channel voice mode. Do not invent voice IDs or imply all profiles sound equally good.

No cloning or streamer imitation. Narrator distinct from source creator. Generate WAV/PCM, chunk long scripts carefully, validate audio is non-empty/non-garbled, verify duration, align using actual alignment or forced alignment/transcription. Never estimate word timing by evenly dividing sentences. Preserve narration WAV and voice metadata for resume. On failure, retry safely and show error; optionally render without narration only if resulting clip remains valid and passes QA.

## 12. Smart vertical editor

Target 1080x1920, 9:16 MP4, H.264/AAC, source-matched 30/60 fps where appropriate. Verify current Shorts/Reels duration rules before release; use conservative presets.

Layouts: facecam TOP + gameplay BOTTOM when both detected; gameplay/screen full-frame when no useful facecam; speaker crop for talking head; split when it preserves context. Stable tracking, safe margins, no layout jitter. Preserve important UI, source watermark and attribution. Smart crop is not enforcement evasion.

Captions: accurate source dialogue; separate narrator captions; burned-in + SRT/VTT; high contrast, 1-2 lines, safe margins; emphasize few words; don't cover faces/UI/text.

Audio: distinct narrator, intelligibility-first mix, duck source only as needed, licensed music/SFX only (music OFF by default until cleared), prevent clipping, check final render.

Pacing: remove dead air only if context, comedy timing, evidence and payoff remain. Purposeful cuts/zooms/transitions, not constant effects.

## 13. Covers and publishing package

Generate 3 truthful cover concepts: curiosity-led, moment-led, explanation-led. Use approved frames and Pillow/SVG. One focal point, usually 2-5 words, central safe area. No fake quote/reaction/outcome. Export separate YouTube and Instagram covers. If thumbnail API unavailable/ineligible, export local cover for manual selection.

YouTube: 5 truthful title choices + recommended title/rationale; accurate description; attribution only from permission record; relevant tags/hashtags; no stuffing/trend bait; category/language suggestion with uncertainty; account owner chooses audience/Made for Kids; accurate altered/synthetic disclosure; export-only default.

Instagram: distinct native caption, relevant hashtags, accurate alt text, separate cover and crop preview. Export-only works without Instagram connection.

Direct publishing is optional, requires current API review, OAuth, scopes, eligibility, owner permission and explicit confirmation. Never publish public by default.

## 14. Rights, originality, factuality and QA gate

Check permission/scope, attribution, commercial use, derivative rights, music/SFX licences, meaningful original commentary, repetitive scripts/scenes/templates, supported factual claims, privacy, truthful metadata/cover, altered-media disclosure, dimensions/codecs/duration, audio clarity/clipping/sync, captions and package completeness.

PASS is not copyright-safe certificate/legal opinion/YPP/platform approval. NEEDS_REVIEW is not ready. BLOCKED must not produce publish-ready folder.

Required errors: NO_PERMISSION_EVIDENCE, PLATFORM_SCOPE_MISMATCH, PERMISSION_EXPIRED, SOURCE_ACCESS_NOT_SUPPORTED, API_AUTH_REQUIRED, API_QUOTA_EXCEEDED, CHAT_SIGNAL_UNAVAILABLE, COMMENTARY_TOO_GENERIC, FACT_UNSUPPORTED, LANGUAGE_MISMATCH, TTS_PROVIDER_NOT_ELIGIBLE, TTS_GENERATION_FAILED, TRANSCRIPTION_LOW_CONFIDENCE, INSUFFICIENT_STRONG_MOMENTS, DISK_SPACE_LOW, MODEL_NOT_INSTALLED, MODEL_HASH_MISMATCH, RENDER_FAILED, QA_FAILED, THUMBNAIL_UPLOAD_PENDING.

Every error: readable reason, next action, diagnostic ID; no secrets.

## 15. Reliability, database and storage

Use migration-managed SQLite and typed schemas for Project, ChannelProfile, SourceAsset, RightsGrant, PlatformConnection, LiveMonitorSession, TranscriptSegment, SceneBoundary, AudioEvent, ChatActivityBucket, EventMap, CandidateClip, CandidateScore, CommentaryScript, NarrationAsset, VoiceProfile, EditPlan, RenderAsset, ThumbnailConcept, PublishingMetadata, PolicyReview, Job, JobEvent and ExportManifest.

Use integer millisecond timestamps consistently. Validate model JSON. Cache by source hash/model revision/settings. Save intermediates, atomic final rename, resumable stage execution, bounded retries, safe cancellation and path sanitization. Preserve originals.

## 16. Hardware and resource management

Target user: Windows 11, 16 GB RAM (single 16 GB stick), laptop may get warm; CPU/GPU exact model unknown. Detect CPU/RAM/GPU/driver/hardware encoders/FFmpeg support/free disk. Don't assume dedicated GPU.

Sequential heavy stages; release memory between models; Low Resource/Balanced/Quality profiles; CPU fallback. Thermal throttle only if reliable sensor values exist. Use proxy previews and render finals only after selection. Benchmark with short original/synthetic assets: ASR speed, LLM latency, TTS real-time factor, render FPS, peak RAM/VRAM and reliable temperature readings. Never invent processing-time estimates.

## 17. UI details

Dashboard: job history, daily target clearly labelled target, PASS/review/blocked counts, storage/model readiness, platform connection state.

New Job: file picker/drop zone, supported source field, permission profile/evidence, output platforms, max clips default 3, advanced options hidden, Create Shorts Pack.

Auto Discover: GTA 6 preset, platform filters, real available metadata, freshness, allowlist, media/permission status, quotas and disconnected states.

Live Monitor: authorized session, transcript/event timeline, audio signals, real chat availability, reconnect state, stop button.

Candidates: ranked cards, timestamps, score breakdown, transcript excerpt, evidence, preview, accept/reject/flag.

Preview Studio: vertical preview, script, narrator voice, captions, crop/layout, audio mix, safe re-render. No manual timeline required.

Publishing Pack: YouTube/Instagram tabs, titles/descriptions/captions/tags/hashtags/covers/alt text, QA state, copy/open buttons.

Settings: channel, voices, model downloads, hardware, platform credentials, output paths, retention, privacy and diagnostics.

Every button works. Provide empty/loading/disconnected/partial/error/success states.

## 18. Export structure

For each PASS clip:
- YouTube_Shorts.mp4
- Instagram_Reel.mp4
- YouTube_Cover.png
- Instagram_Cover.png
- YouTube_Metadata.txt and .json
- Instagram_Caption.txt
- Instagram_Hashtags.txt
- Instagram_AltText.txt
- Captions.srt and .vtt
- Source_Attribution.txt
- Rights_Manifest.json
- QA_Report.html
- Preview.jpg
- Commentary_Script.txt
- Narration_Metadata.json

One project folder contains up to 3 clip folders, Project_Summary.html and Project_Manifest.json. Blocked/review files go to separate review area and are never labelled upload-ready.

## 19. Testing and acceptance

Use only original/synthetic/licensed fixtures.

Unit: timestamp bounds, ranking/dedupe, permission scope/expiry, JSON validation, path sanitization, error redaction, audio event math, chat normalization/missingness, script duration, job transitions.

Integration: ffprobe, audio extraction, ASR English sample, deterministic/mock LLM, Kokoro short generation if model installed, caption alignment/SRT, vertical FFmpeg render, output verification, SQLite resume, no-permission block, API/model unavailable states.

E2E acceptance:
A. Authorized local source through analysis, candidate ranking, English original script, TTS, render, QA, export.
B. No permission blocks publish-ready export.
C. Commentary provides specific value.
D. New viewer understands setup/event/payoff.
E. Crop preserves face/gameplay/UI.
F. Captions match speech and remain safe.
G. Audio intelligible/unclipped.
H. Five title choices and metadata are truthful.
I. Covers match real event.
J. Duplicates are flagged.
K. Interrupted render resumes.
L. Complete package exists.
M. Local mode works without platform credentials.
N. Missing chat signal labelled unavailable.
O. Clean Windows install/launch/job/uninstall smoke test.

## 20. Phased implementation

0: inspect empty repo, feature branch, conventions, docs, CI.  
1: desktop shell, Python worker, SQLite, rights form, local source intake, FFmpeg probe/basic export.  
2: ASR, audio event map, scenes, candidates and ranking.  
3: LLM scripts/critic, Kokoro adapter, voice audition, alignment.  
4: smart crop/layout/captions/audio mix/vertical render/preview.  
5: metadata, covers and export packager.  
6: rights, factuality, originality, repetition, privacy, retries, recovery and security.  
7: official discovery/live integrations, chat where available, OAuth/scopes/quotas.  
8: Windows installer, first-run model downloads, clean install tests, notices and release.

Manual/local mode must remain complete when APIs are disconnected. Do not build fake integrations.

## 21. GitHub workflow

Repository: ven​zorx/clipper (owner-confirmed empty repository; default main). Use a descriptive feature branch; no force-push. Commit logical changes. Never commit secrets/media/weights/cache/exports. Run tests and CI. Push branch and open PR to main; keep draft while CI or Windows smoke tests remain incomplete. Do not auto-merge. Report branch, exact commit SHA, PR URL, test results and blockers. Never claim a push/build/test unless verified.

## 22. Required documentation/release

README, PRODUCT_SPEC.md, ARCHITECTURE.md, USER_GUIDE.txt, SETUP_GUIDE.md, TROUBLESHOOTING.md, SECURITY_AND_PRIVACY.md, MODEL_AND_THIRD_PARTY_NOTICES.md, PLATFORM_INTEGRATIONS.md, ACCEPTANCE_TESTS.md, IMPLEMENTATION_STATUS.md, CHANGELOG.md, PowerShell dev/build/verify scripts, CI workflows, installer and smoke-test record.

Final report lists implemented modules, tests and outcomes, installer path, setup steps, required credentials, actual benchmark data and outstanding limitations.

## 23. Definition of Done

A usable v1 requires: installed desktop shortcut; setup wizard; local authorized source import; strict rights record/gate; English ASR; explainable candidates; best-three quality selection; original English scripts and critique; multiple tested Kokoro English voices; voice alignment/captions; 9:16 editing including facecam/gameplay when present; audio QC; YouTube/Instagram package; rights/originality/factuality/repetition/privacy/technical QA; complete export; resume/recovery; local operation without platform credentials; honest external integration states; clean Windows installer test; complete docs/licence notices; CI pass; branch pushed and PR created.

Not required/never guaranteed: viral reach, exactly 3 clips per source, copyright/strike immunity, YPP, unlimited API access, arbitrary stream access, exact processing time on unspecified hardware.

## 24. Start now

Do not reply with only a plan. Inspect repo/workspace, confirm default branch and empty state, create a feature branch, then implement Phase 0 and Phase 1 and continue sequentially. After every phase run tests, record commands/results, update implementation status and commit. If blocked by API credentials, platform capability, Windows host, model licence or media authorization, implement safe local fallback and mark the integration blocked. Never fake success.

### AI prompt contracts

Candidate analyser: use timestamped transcript, scenes, audio events and authorized live-chat if available. Return up to 8 coherent moments with exact timestamps, setup/context/event/payoff, viewer value, visual refs, audio risks, commentary angle, confidence and score. Never fabricate facts or permission.

Script writer: English hook, context, specific analysis and payoff. No paraphrase-only, no invented facts, quote, reaction, motivation or outcome. Label opinion/uncertainty. Match duration. Return JSON with claims/evidence/word count/quality.

Script critic: strict check for first-second relevance, truthful curiosity, context, clarity, pace, originality, facts, footage fit and payoff. Penalize generic hooks, filler, unresolved bait and repetition. No virality guarantee.

Metadata writer: five truthful titles plus recommendation/rationale, accurate description, relevant tags/hashtags, native Instagram caption and alt text, three covers. No false urgency or unrelated trends.

QA reviewer: rights, attribution, music licence, original value, factuality, repetition, privacy, disclosure, metadata, video/audio/captions/covers/package. Return PASS/NEEDS_REVIEW/BLOCKED with evidence. Never certify copyright safety, monetization or reach.
