# Two-minute demonstration

1. Open the local app. Mention the persistent prototype label and synthetic-case boundary.
2. Select **Try a sample question**, then **Start huddle**. The sample concerns reviewing breast-cancer evidence, not a patient-specific treatment recommendation.
3. Review specialty, condition, topic, and intent. Explain that classification is scripted for this demo.
4. Choose **Continue to evidence**. Show the public NCI links and source scope/date labels.
5. Show the explicitly fictional expert and explain that 94% is an illustrative relevance score, not medical certainty.
6. Click **Request huddle**. This opens the simulated expert workspace; no real clinician is contacted.
7. Type a response or choose **Use simulated response**. Optional voice transcription works when the browser and microphone support it.
8. Choose **Create huddle brief**. Show the separate evidence, opinion, takeaways, uncertainty, and references.
9. Download or copy the brief. Playback is an optional synthetic reading, not a recorded clinician.
10. Open **Question graph**, change the specialty, and show the accessible data table. These are illustrative counts, not real engagement analytics.

Close: “Don’t send physicians another message. Answer the question they’re actually asking.”

## Fallbacks

- No voice support or denied microphone → typed input.
- No matching demo case → visible evidence gap and no expert match.
- Backend unavailable → visible error with an explicit demo switch on creation.
- Clipboard unavailable → download the text brief.
- Browser storage unavailable → in-memory session continues.

## Milestone handoff

COMPLETED: Six responsive screens, demo lifecycle, voice transcription fallback, brief export, synthetic graph, proposed API adapter, and tests.

SCREEN: HCP home, question understanding, evidence + expert, expert response, Huddle Brief, Question Graph.

API REQUIRED: Three proposed Huddle endpoints described in API.md; teammate agreement and authentication remain necessary.

MOCK DATA: Scripted breast-cancer case, NCI resource descriptions, fictional Dr. Maya Patel, template brief, synthetic analytics.

BLOCKERS: Real backend models/services, live retrieval/synthesis, expert identity and routing are not implemented by this frontend milestone.

NEXT: Agree on the backend contract, integrate development endpoints, then validate the combined end-to-end system.
