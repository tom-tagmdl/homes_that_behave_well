# Interaction Flow: Concierge Artwork History (Context-Aware Response)

## Purpose

This interaction demonstrates how Concierge and Asset Intelligence work together to:

- resolve context (room)
- disambiguate between multiple assets
- adapt responses based on audience (guest vs owner)
- provide a clear and explainable experience

---

## Scenario Overview

A guest is in a room containing multiple pieces of artwork.

The guest asks:

"What is the history of this artwork?"

The system must:

- determine which artwork is being referenced
- adapt the response for a guest audience
- retrieve the correct description
- present it clearly

---

## Environment Context

Room:

- area_id: living_room

Assets in room:

- painting_1: Landscape Painting
- painting_2: Abstract Artwork
- painting_3: Portrait Painting

Room awareness:

- multiple valid assets present
- disambiguation required

---

## Step 1: User Input

User speaks:

"What is the history of this artwork?"

Input is captured by:

- voice system
- routed to Concierge

---

## Step 2: Context Resolution

Concierge determines:

- current room from presence signals
- active area_id: living_room

Rules:

- context must be deterministic
- no guessing across rooms

---

## Step 3: Audience Detection

System identifies user role:

- role: guest

This influences:

- messaging tone
- description content
- level of detail

Rules:

- guest descriptions must be simpler
- owner descriptions may include deeper detail

---

## Step 4: Asset Disambiguation

Problem:

- 3 artworks exist in the room

Concierge must resolve:

- which asset is being referenced

Approaches (in order of confidence):

1. recent interaction context (e.g., user looking at asset detail)
2. proximity (BLE tag, presence detection if available)
3. visual reference (future capability)
4. clarification prompt (fallback)

---

## Step 5: Clarification (If Needed)

If confidence is not sufficient:

Concierge asks:

"Which artwork are you asking about? The landscape, the abstract, or the portrait?"

User responds:

"The landscape"

---

## Step 6: Asset Resolution

Concierge resolves:

- asset_id: landscape_painting

Calls Asset Intelligence:

- get asset metadata
- get descriptions
- get history

---

## Step 7: Description Selection

Asset contains:

descriptions:

- guest_description
- owner_description

Concierge selects:

- guest_description

Rules:

- must match user role
- must be appropriate for context
- must not expose unnecessary detail

---

## Step 8: Response Generation

Concierge constructs response:

Example:

"This landscape painting was created by a regional artist and reflects early 20th-century countryside scenes. It was acquired as part of a private collection and is known for its use of natural light and color."

---

## Step 9: Delivery

Concierge determines delivery:

- correct room speaker
- apply messaging rules (Info level, non-urgent)

Actions:

- duck/pause audio if needed
- speak response
- restore audio state

---

## Step 10: Optional Follow-Up

Concierge may offer:

- "Would you like to hear more about the artist?"
- "Would you like to see additional details?"

Rules:

- follow-ups must be optional
- no forced interaction
- no overwhelming the user

---

## Failure Handling

If asset cannot be resolved:

Concierge responds:

"I’m not sure which artwork you’re referring to. Could you point me to it or describe it?"

If no description available:

"This artwork does not have a description configured yet."

---

## Architectural Alignment

Concierge:

- resolves room context
- determines user role
- orchestrates interaction
- selects appropriate content

Asset Intelligence:

- stores asset data
- provides descriptions and history
- does not format interaction

---

## Key Principles Demonstrated

- deterministic context resolution
- clear separation of responsibilities
- audience-aware messaging
- graceful disambiguation
- non-intrusive interaction
- explainable behavior

---

## Final Outcome

The system:

- understands where the user is
- identifies what they are referring to
- adapts the response based on who they are
- delivers information clearly and calmly

The result is a natural, intelligent, and predictable interaction that feels like a knowledgeable guide rather than a technical system.