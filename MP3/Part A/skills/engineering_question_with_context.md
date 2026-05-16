name: engineering-question-with-context
description: >
Answer an engineering question that mixes a Ridgeline-internal
reference with a quantitative calculation. Orchestrates two tools:
query_ridgeline_rag for project history, billing, and internal
standards, and convert_units for unit-system translation. The goal
is one synthesized engineering answer, not retrieved chunks pasted
next to a raw converted number.
Skill: Engineering Question with Project Context
When to use this skill
Use this when the user's question combines two or more of:

a reference to a specific Ridgeline project, billing rate, or
internal standard
a numeric quantity that may need converting between US customary
and SI
a comparison between something Ridgeline does and broader
engineering practice.

If the question is purely general engineering knowledge with no
Ridgeline reference, don't call the RAG. If there's no number in the
question, don't call the converter. Don't call tools speculatively
"in case."
Steps

Read the question and write down (mentally) which parts are
Ridgeline-specific, which are general engineering knowledge, and
which are unit conversion. That tells you which tools to call.
Call query_ridgeline_rag first for any Ridgeline-specific part.
Phrase the query as a focused semantic search — the project name
plus what you're trying to find, not the user's whole question.
Call convert_units for every numeric quantity that needs to
appear in the answer in the other unit system. Always go through
the tool — even when it seems easy, the point is that the number
is auditable.
Synthesize. Tie the retrieved info to the question, don't dump
chunks. The converted number goes inline in an engineering
sentence ("the 500 lbf load — about 2.22 kN — is within…"), not
appended as a footnote.
If the RAG didn't return anything relevant, say so directly:
"Ridgeline's documents don't cover this." Don't make up a
Ridgeline practice from training data.

What to flag

A value given in one unit system that the user implicitly needs in
the other to be able to compare it with retrieved context (user
says 500 lbf, the RAG result is in N).
Retrieved chunks that look related but don't actually answer the
question. Surface the gap; don't paper over it.
A mismatch between the project the user named and the project the
RAG actually returned. Name the project the chunks came from.

What NOT to do

Don't skip the RAG just because the question "sounds general." If
the user named a Ridgeline project, retrieval is mandatory — the
training-data answer about that project is by definition wrong.
Don't skip the converter and convert in your head. The tool is
cheap and the conversion is then auditable in the transcript.
Don't paste retrieved chunks verbatim as the answer. The chunks
are evidence; the answer is engineering judgment that uses them.

Output format
One short paragraph (3–6 sentences) that answers the question, with
converted numbers inline and Ridgeline context woven through. End
with a one-line citation listing the doc_id of any RAG chunk you
actually relied on.
