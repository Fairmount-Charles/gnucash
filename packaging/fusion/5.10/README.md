# Fusion Debian GnuCash 5.10 repair set

These downstream source patches target Debian's GnuCash 5.10 package. The fork's
root source tracks a newer upstream stable release and is not the deployed 5.10
engine. Apply the numbered patches in order to pristine 5.10 source, then build
matching gnucash, gnucash-common, and python3-gnucash packages. Preserve Debian
packaging inputs and all upstream license/copyright notices.

1. Namespace-scoped persistent transaction external identities; copies clear them.
2. Collision-safe native XML backup filenames without overwriting older backups.
3. Existing authoritative invoice GUID exposed through SWIG and the typed Python
   Invoice.GetGUID wrapper; adapted from this fork's invoice binding repair.

4. Existing authoritative lot GUID exposed through SWIG and typed GncLot.get_guid.
   Required for posted invoice/payment lot identity readback.

This directory is the authoritative editable 5.10 repair set. Server-framework
patch copies are historical compatibility artifacts until replaced by references
here. Provider semantics and retained qualification journeys remain owned by
fc-fusion-server-framework-source/fc_gnucash; build/deployment realization and
release evidence remain owned by fc-infrastructure.

Qualification must use the worker interpreter and real disposable XML books:
provider semantic qualification, transaction lost-result/re-entry, and the invoice,
posting, payment, reconciliation, backup and isolated-restore journey. Build/import
success alone does not establish governed Pipeline or tenant-isolation acceptance.
Retain prior Debian packages for rollback and never overwrite active accounting books.

Do not add credentials, books, customer data, worker grants, or Fusion authorization
policy to GnuCash. Repository revisions are build provenance, not runtime eligibility.

5. Existing engine-owned Book string-option getters/setters exposed through SWIG.
   This enables native persistent fiscal policy without a sidecar accounting store.
   The API and C ABI already exist; this repair changes binding declarations only.

The fifth repair was built as Debian 1:5.10-0.1+fc5. Its Python 3.13 bindings
were also qualified with the installed fc4 engine libraries on the dedicated
Accounting host. Real disposable-book provider C, D and E journeys passed;
the retained C journey includes closed-period write denial, linked journal
reversal and reopening, and E verifies policy survives backup/isolated restore.
This is native capability evidence, not live Runtime or release acceptance.
