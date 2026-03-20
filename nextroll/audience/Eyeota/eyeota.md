# Eyeota

[Pitch](https://docs.google.com/document/d/1MfonmYAOjezifIj-f7nr7yHI5JDaKS91FuOQB7u89wg/edit?tab=t.0)

## Experian

[Experian Provided Documentation](https://adroll.atlassian.net/wiki/spaces/EN/pages/4515463172/Experian+Provided+Documentation)

[Lookalike Segmentation Using Experian](https://adroll.atlassian.net/wiki/spaces/EN/pages/4531879957/Lookalike+Segmentation+Using+Experian)

## Eyeota Info

[Preliminary Info](https://adroll.atlassian.net/wiki/spaces/EN/pages/4174774274/Preliminary+Info)

[Eyeota Global Audience Working Plan](https://adroll.atlassian.net/wiki/spaces/EN/pages/4587454465/Eyeota+Global+Audience+Working+Plan)

## Questions

### IFAIK, in Experian, the data is shaped as a graph where the root is the Living Unit ID (LUID), so it the hierarchy is like this: LUID => Household_ID => Device_ID [Cookie, HEM, or MAID]. But with Eyeota, I can’t see (or I haven’t found in Confluence) any relational information about the IDs. So, my question is: In Eyeota, is the data flat with no hierarchy or relation as in Experian?

Correct, the data is indeed flat with no Household hierarchy or relation as in Experian

### Another question, I only see one partition for Cookies. Should we say these are NextRoll Cookies?

Yes, the cookie file should consist of NextRoll tpc based on the user sync we have with Eyeota (RTI-17067)

### DPID stands for?

DPID is a type of CTV_IFA which stands for Device Platform Identifier

### A CTV audience should be the union of AAID_CTV + AFID + IDFA_CTV + RIDA + TIFA?

Correct, CTV audience identifiers include any of the following:  `AAID_CTV`, `AFAI`, `DPID`, `IDFA_CTV`, `MSAI`, `RIDA`, or `TIFA`

### MAID, should be any values in AADI, AFAID and MSID?

MAID audience identifiers should only the following identifiers: `AAID`, `IDFA`

### I can’t see IP addresses in this dataset. If IPs are not part of Eyeota dataset, how should we do geo targeting other than the country the IDs belongs to? 

`country_iso_code` should be used for forecasting audience avails by region, but we should be using the IP address in bid requests for targeting.
