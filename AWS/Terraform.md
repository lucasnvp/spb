
#### How to Fix 

<font color="red">Error: Failed to decode resource from state </font>

Yeah, ok so the only real solution other then rolling back is to do something like this:

`terraform state pull >> state.json`

then edit that json to remove the now removed attributes from being managed.

You will have to manually increment the  `"serial": [number],` at the top of that json file so terraform knows you are incrementing the state.

Luckily there is a some validation on the terraform state push command so when you do a:

`terraform state push state.json`

It shouldn't let you break your remote state.

If your state is massive it can be very tedious, I would recommend if you are running any regex find/replace to save a copy and do a diff to verify the changes, also then you have a copy of the original state to fall back to.

Luckily our terraform repos make heavy use of terraform_remote_state to break our state into small manageable pieces, which is read only. So far it has not been an issue using terraform_remote_state with a .13 binary from a .12 managed state backend. So we can make fixes incrementally.