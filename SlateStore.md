# SlateStore Protocol

One of the often mentioned problems with grin is impossibility of securely producing transaction while two parties are not online simultaneously. It is possible to use messenger applications to exchange slatepacks but that requires to partially reveal one's identity. Inspired by [this forum post](https://forum.grin.mw/t/the-non-existing-problem-with-interactive-transactions-ux-rant/8515/15?u=renzokuken) I had an idea to draft a protocol allowing to outsource the work of online listener in exchange for a fee paid in grin.

Discussion on the [grin forum](https://forum.grin.mw/t/slatestore-protocol/9087).

## Example

Let us consider a scenario involving three participants, Alice, Bob and Carol. Alice want's to send 5ツ to Bob and agrees to cover additional 0.023ツ network fee, but the problem is both Alice and Bob live in differrent timezones and they are rarely online simultaneously. Carol offered them help as a trustless intermediary who would help them interact for a small fee of 0.01ツ. The numbers here have been chosen to be arbitrary just for an example.

Protocol would go as follows

1. Alice prepares a multi-signature transaction with own input and three outputs, the 5ツ for Bob, the 0.01ツ for Carol and change for herself.
2. Alice interacts with Carol to sign the transaction, then goes offline
3. Carol waits online until Bob appears, provides him the transaction and collects the signature
4. Carol waits for Alice to appear online again so that Alice can finalize the transaction

## Why it works

Carol has an incentive to stay online for Bob as without interaction with Bob Carol wouldn't be able to get the 0.01ツ. This also happens to be in the best interest of both Alice and Bob.

## Open questions

1. Is it possible to make Carol finalize the transaction? That would elliminate step (4).
2. How to efficiently let Bob prove being the receiver without revealing own slatepack address?
