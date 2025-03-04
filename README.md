# DataSaveService

Simplifies the usage of [ProfileStore by loleris](https://devforum.roblox.com/t/profilestore-save-your-player-data-easy-datastore-module/3190543).

## Methods
### SetSilentMode

Toggles silent mode.
Silent mode toggles print statements from DataSaveService in the output.
Errors and warnings will always be visible.

#### Parameters
| Paremeter | Type | Description | 
| ----------- | ----------- | ----------- |
| `enabled` | `boolean?` | Sets silent mode to `enabled`. |

#### Retuns
`nil`


### SetTemplate

Sets the template for `Profile:Reconcile()`.

#### Parameters
| Paremeter | Type | Description | 
| ----------- | ----------- | ----------- |
| `template` | `{any}` | The table to set the `ProfileStore`'s template to. |

#### Returns
`nil`


### GetTemplate

Gets the template used by `Profile:Reconcile()`.


### SetProfileStoreName

Sets the name of the `ProfileStore`.
If no name is set DataSaveService defaults to using **MAIN_PROFILE**.

#### Parameters
| Paremeter | Type | Description | 
| ----------- | ----------- | ----------- |
| `storeName` | `string` | The name to set `ProfileStore` to. |

#### Returns
`nil`


### SetProfileKeyTemplate
Sets the template for Profile keys to follow.
***%s*** will be replaced by the Player's UserId.
If no template is set DataSaveService will default to "%s".

#### Parameters
| Paremeter | Type | Description | 
| ----------- | ----------- | ----------- |
| `keyTemplate` | `string` | The template to use for keys. |

#### Returns
`nil`


### CreateProfileStore
Starts the module and automatically loads the Profiles of all Players that are in the game along with loading Profiles of players who join after.
A template must first be set using `DataSaveService:SetTemplate()`.
This method can only be called once.

#### Returns
`ProfileStore`


### GetProfileStore
Returns the `ProfileStore`. Yields until `DataSaveService:CreateProfileStore()` is called and has run.

#### Returns
`ProfileStore`


### GetProfile
Returns the `Profile` associated with the `Player`. Returns nil if no `Profile` is found.

#### Parameters
| Paremeter | Type | Description | 
| ----------- | ----------- | ----------- |
| `player` | `Player` | The `Player` to find the `Profile` of. |

#### Returns
`Profile` or `nil`


### WaitForProfile
Yields until the Profile for `player` is found. Returns `nil` if `player` leaves before their `Profile` loads.

#### Parameters
| Paremeter | Type | Description | 
| ----------- | ----------- | ----------- |
| `player` | `Player` | The `Player` to find and wait for the `Profile` of. |

#### Returns
`Profile` or `nil`


### GetProfiles
Returns a table of all of the `Profiles` currently loaded with `Player` used as the index.

#### Returns
`{[Player]: Profile}`


### GetProfileKey
Returns the key based on the provided UserId.

#### Parameters
| Paremeter | Type | Description | 
| ----------- | ----------- | ----------- |
| `userId` | `number` | The `UserId` to be used for the key. |

### Returns
`nil`




## Events
### ProfileAdded
```
DataSaveService.ProfileAdded:Connect(function(player: Player)
  local profile = DataSaveService:GetProfile(player) --> Profile
end)
```
The `ProfileAdded` event will fire when a new `Profile` is added.

### ProfileRemoving
```
DataSaveService.ProfileRemoving:Connect(function(player: Player)
  local profile = DataSaveService:GetProfile(player) --> Profile
end)
```
The `ProfileRemoving` event will fire right before a Profile gets removed. This may fire on server shutdown causing code to not run before it closes.

### ProfileRemoved
```
DataSaveService.ProfileRemoved:Connect(function(player: Player)
  local profile = DataSaveService:GetProfile(player) --> nil because the profile has been removed.
end)
```
The `ProfileRemoved` event fires right after a Profile is removed and released. This may fire on server shutdown causing code to not run before it closes.


## Classes
[ProfileStore](https://madstudioroblox.github.io/ProfileStore/api/#profilestore)

[Profile](https://madstudioroblox.github.io/ProfileStore/api/#profile)
