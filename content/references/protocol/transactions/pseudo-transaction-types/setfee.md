---
html: setfee.html
parent: pseudo-transaction-types.html
blurb: Change global reserve and transaction cost settings.
labels:
  - Fees
---
# SetFee

A `SetFee` [pseudo-transaction](pseudo-transaction-types.html) marks a change in [transaction cost](transaction-cost.html) or [reserve requirements](reserves.html) as a result of [Fee Voting](fee-voting.html).

**Note:** You cannot send a pseudo-transaction, but you may find one when processing ledgers.

## Example {{currentpage.name}} JSON

```json
{
    "Account": "rrrrrrrrrrrrrrrrrrrrrhoLvTp",
    "BaseFee": "000000000000000A",
    "Fee": "0",
    "ReferenceFeeUnits": 10,
    "ReserveBase": 20000000,
    "ReserveIncrement": 5000000,
    "Sequence": 0,
    "SigningPubKey": "",
    "TransactionType": "SetFee",
    "date": 439578860,
    "hash": "1C15FEA3E1D50F96B6598607FC773FF1F6E0125F30160144BE0C5CBC52F5151B",
    "ledger_index": 3721729,
}
```

{% include '_snippets/pseudo-tx-fields-intro.md' %}
<!--{# fix md highlighting_ #}-->

| Field               | JSON Type        | [Internal Type][] | Description     |
|:--------------------|:-----------------|:------------------|:----------------|
| `BaseFee`           | String           | UInt64            | The charge, in drops of XRP, for the reference transaction, as hex. (This is the [transaction cost](transaction-cost.html) before scaling for load.) |
| `ReferenceFeeUnits` | Unsigned Integer | UInt32            | The cost, in fee units, of the reference transaction |
| `ReserveBase`       | Unsigned Integer | UInt32            | The base reserve, in drops |
| `ReserveIncrement`  | Unsigned Integer | UInt32            | The incremental reserve, in drops |
| `LedgerSequence`    | Number           | UInt32            | _(Omitted for some historical `SetFee` pseudo-transactions)_ The index of the ledger version where this pseudo-transaction appears. This distinguishes the pseudo-transaction from other occurrences of the same change. |


If the _[XRPFees amendment][]_ is enabled, `SetFee` pseudo-transactions use these fields instead:

| Field                   | JSON Type | [Internal Type][] | Description     |
|:------------------------|:----------|:------------------|:----------------|
| `BaseFeeDrops`          | String    | Amount            | The charge, in drops of XRP, for the reference transaction. (This is the [transaction cost](transaction-cost.html) before scaling for load.) |
| `ReserveBaseDrops`      | String    | Amount            | The base reserve, in drops |
| `ReserveIncrementDrops` | String    | Amount            | The incremental reserve, in drops |
| `LedgerSequence`        | Number    | UInt32            | _(Omitted for some historical `SetFee` pseudo-transactions)_ The index of the ledger version where this pseudo-transaction appears. This distinguishes the pseudo-transaction from other occurrences of the same change. |


{% include '_snippets/setfee_uniqueness_note.md' %}

<!--{# common link defs #}-->
{% include '_snippets/rippled-api-links.md' %}
{% include '_snippets/tx-type-links.md' %}
{% include '_snippets/rippled_versions.md' %}
