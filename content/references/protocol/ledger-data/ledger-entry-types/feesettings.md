---
html: feesettings.html
parent: ledger-entry-types.html
blurb: Singleton object with consensus-approved base transaction cost and reserve requirements.
labels:
  - Fees
---
# FeeSettings
[[Source]](https://github.com/XRPLF/rippled/blob/master/src/ripple/protocol/impl/LedgerFormats.cpp#L115-L120 "Source")

The `FeeSettings` entry contains the current base [transaction cost](transaction-cost.html) and [reserve amounts](reserves.html) as determined by [fee voting](fee-voting.html). Each ledger version contains **at most one** `FeeSettings` entry.

## Example {{currentpage.name}} JSON

```json
{
   "BaseFee": "000000000000000A",
   "Flags": 0,
   "LedgerEntryType": "FeeSettings",
   "ReferenceFeeUnits": 10,
   "ReserveBase": 20000000,
   "ReserveIncrement": 5000000,
   "index": "4BC50C9B0D8515D3EAAE1E74B29A95804346C491EE1A95BF25E4AAB854A6A651"
}
```

## {{currentpage.name}} Fields

In addition to the [common fields](ledger-entry-common-fields.html), the `{{currentpage.name}}` ledger entry has the following fields:

| Name                | JSON Type | [Internal Type][] | Required? | Description            |
|:--------------------|:----------|:------------------|:----------|:-----------------------|
| `BaseFee`           | String    | UInt64            | Yes       | The [transaction cost](transaction-cost.html) of the "reference transaction" in drops of XRP as hexadecimal. |
| `Flags`             | Number    | UInt32            | Yes       | A bit-map of boolean flags enabled for this object. Currently, the protocol defines no flags for `FeeSettings` objects. The value is always `0`. |
| `LedgerEntryType`   | String    | UInt16            | Yes       | The value `0x0073`, mapped to the string `FeeSettings`, indicates that this object contains the ledger's fee settings. |
| `ReferenceFeeUnits` | Number    | UInt32            | Yes       | The `BaseFee` translated into "fee units". |
| `ReserveBase`       | Number    | UInt32            | Yes       | The [base reserve](reserves.html#base-reserve-and-owner-reserve) for an account in the XRP Ledger, as drops of XRP. |
| `ReserveIncrement`  | Number    | UInt32            | Yes       | The incremental [owner reserve](reserves.html#base-reserve-and-owner-reserve) for owning objects, as drops of XRP. |

**Warning:** The JSON format for this ledger entry type is unusual. The `BaseFee`, `ReserveBase`, and `ReserveIncrement` indicate drops of XRP but ***not*** in the usual format for [specifying XRP][Currency Amount].


If the _[XRPFees amendment][]_ is enabled, the `FeeSettings` object has these fields instead:

| Name                    | JSON Type | [Internal Type][] | Required? | Description            |
|:------------------------|:----------|:------------------|:----------|:-----------------------|
| `BaseFeeDrops`          | String    | Amount            | Yes       | The [transaction cost](transaction-cost.html) of the "reference transaction" in drops of XRP. |
| `Flags`                 | Number    | UInt32            | Yes       | A bitmap of boolean flags enabled for this object. Currently, the protocol defines no flags for `FeeSettings` objects. The value is always `0`. |
| `LedgerEntryType`       | String    | UInt16            | Yes       | The value `0x0073`, mapped to the string `FeeSettings`, indicates that this object contains the ledger's fee settings. |
| `ReserveBaseDrops`      | String    | Amount            | Yes       | The [base reserve](reserves.html#base-reserve-and-owner-reserve) for an account in the XRP Ledger, as drops of XRP. |
| `ReserveIncrementDrops` | String    | Amount            | Yes       | The incremental [owner reserve](reserves.html#base-reserve-and-owner-reserve) for owning objects, as drops of XRP. |


## {{currentpage.name}} Flags

There are no flags defined for the `{{currentpage.name}}` entry.


## FeeSettings ID Format

The ID of the `FeeSettings` entry is the hash of the `FeeSettings` space key (`0x0065`) only. This means that the ID is always:

```
4BC50C9B0D8515D3EAAE1E74B29A95804346C491EE1A95BF25E4AAB854A6A651
```


<!--{# common link defs #}-->
{% include '_snippets/rippled-api-links.md' %}
{% include '_snippets/tx-type-links.md' %}
{% include '_snippets/rippled_versions.md' %}
