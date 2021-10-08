## Minecraft command placeholders, shorthands
## Selectors

advancements (a):
  [ns/]id=b        - id is set
  [ns/]id={cond=b} - matches condition

coordinates (c):
  'float'  - absolute (x, y, z)                      ~/^ are shorthands for ~0/^0 respectively
  '~float' - relative (dx, dy, dz)
  '^float' - reference frame (sway, heave, surge)     ^ and abs/~ coordinates cannot be mixed

ranges (ir,fr):
  i/f        - val = i/f
  [i/f1]..[i/f2] - [i/f1 <] val [< i/f2]

predicate (p):
  ns:id

selectors:
  @s  - self
  @e  - all entities
  @a  - @e[type=player]
  @r  - @e[type=player,sort=random,limit=1]
  @p  - @e[type=player,sort=nearest,limit=1]

selector filters:
sort=#            - sortmethod can be nearest, furthest, arbitrary (id) [default], random (shuffle)
limit=i           - filter only first n hits [default=no limit]
type=t            - having type entityid or #tag; can be specified multiple times

x=c, y=c, z=c     - at coordinates, [omitted components default to ~, do not filter if none of the coordinates present]
dx=c, dy=c, dz=c  - in a box defined by points (x;y;z) and (x+dx;y+dy;z+dz)
x_rotation=fr     - having view declination (in degrees,-90 is zenith, 90 is nadir)
y_rotation=fr     - having facing rotation (in degrees,-180 is north, -90 is east, 0 is south [%360+180])

gamemode=[!]#     - (not) in gamemode, can be spectator,adventure,survival,creative
name=[!]s         - (not) having name
level=ir          - having the xp level in range
team=[!]s         - (not) in team; filter teamless with nullstring
scores={s=ir}     - having registered scoreboard value within intrange
tag=s             - (not) having custom tag (=== nbt={Tags:[t]})
nbt=json          - matching nbt stucture
advancements=a    - having made the advancement a
predicate=p

text formatting
we commands
wg commands
cb ics


@keepitem ingr | replace <item> / replace damage int
@cloneingredient enchants

anvil
@keepitem golden_hoe | replace golden_hoe
a golden_hoe
b book
@cloneingredient enchants
  = book
