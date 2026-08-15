# Method Provenance Record

Public, minimal, append-only record of authorship, chronology, and file integrity
for works published by Vladimir Kostrov (Vlad.Agni) — ORCID: https://orcid.org/0009-0006-8670-2442

**What this repository is:** a small, publicly verifiable record tying together
Zenodo DOIs, ORCID attribution, and exact file hashes for each publication —
so that anyone can independently confirm *what* was published, *when*, and
that the files have not been altered since.

**What this repository is NOT:** the development history of the underlying
work. Drafts, internal review, evidence gathering, and course materials are
kept in a separate private location. This repo publishes what is already
public via Zenodo, and, when created, cryptographic commitments to scoped
private evidence snapshots — the state of documents relevant to the
method's origin, as they existed on a given date (see
`evidence-commitments/`) — something Zenodo does not capture on its own.

## Structure

```
publications/
  <work-slug>/
    v<version>/
      PUBLICATION_RECORD.md   — facts only: title, author, ORCID, DOI, dates, SHA-256

evidence-commitments/
  <date>/
    EVIDENCE_COMMITMENT.txt   — public-facing commitment: scope description, source
                                 repository HEAD, file count, and SHA-256 of a private
                                 evidence archive. The archive's actual contents (which
                                 documents, their names, their text) are NOT published
                                 here — only the fact that a specific cryptographically
                                 fixed set exists, and its hash. Any later alteration of
                                 that archive would be detectable through its hash.

  (Not yet created as of this repo's first commit — added the day the
  private evidence snapshot is actually built and hashed, with that day's
  real date, not before.)
```

## How to verify a publication

1. Open the `PUBLICATION_RECORD.md` for the work.
2. Download the files from the Zenodo record URL listed there.
3. Compute SHA-256 of each downloaded file (`sha256sum <file>`).
4. Compare against the hashes listed in the record — they must match exactly.

## How an evidence commitment works

Each `EVIDENCE_COMMITMENT.txt` publicly fixes the SHA-256 of a private,
scoped archive of documents relevant to a specific publication's origin.
Publishing the hash here — visible to anyone from that point on — means
that archive cannot later be silently altered and presented as the same
snapshot: any change to even one byte changes the hash. If ever needed,
the private archive can be produced and its hash checked against what is
recorded here. (Git's own internal commit-date field is client-set and is
not by itself treated as a trusted timestamp — the corroboration is public
visibility from the point of publication onward, not that field.)

This does **not** independently verify the dates of individual documents
inside the archive (internal dates can be set by hand) — it publicly fixes
the hash of this exact content from that point onward, establishing a
publicly observable checkpoint rather than an independently verified date
for anything inside it.

## Scope note on copyright and method claims

This record establishes *public provenance and publication chronology* —
when a specific published expression of the method became publicly
recorded, and that its files have not been altered since. It does not, and
cannot, claim exclusive rights over the underlying ideas, procedures, or
techniques described — copyright protects a particular expression, not the
method itself. See the Prior-art Note publication for the explicit,
bounded scope claim.

Related: [Method Definition v1.0](https://doi.org/10.5281/zenodo.21931565) |
[Prior-art Note v1.0](https://doi.org/10.5281/zenodo.21935637)
