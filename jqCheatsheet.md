Step 1:

save some well formed json object to a file (I'll be using `campaignScratch` as an example)

step 2:

hack on stuff

Delete part of a json object: `jq 'del(.field)'`

Example:
```
cat campaignScratch | jq 'del(.campaign.memberships)' > temp
rm campaignScratch
mv temp campaignScratch
```


Add a new field to a json object: `js '. + {"field": "value"}'`

Example:
```
cat campaignScratch | jq '. + {memberships: [ { ids: [], limitations: [], placements: [], user_criteria: [], merchant_criteria: [], type: "MEMBERSHIP_ENTITY_TYPE_GLOBAL", promotion: null, created_by: null, created_at: null, id: null }]}'
