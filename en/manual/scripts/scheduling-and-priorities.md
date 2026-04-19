# Scheduling and priorities

<span class="badge text-bg-primary">Beginner</span>
<span class="badge text-bg-success">Programmer</span>

Stride doesn't run scripts simultaneously; they run one at a time. Where scripts depend on each other, you should make sure they run in the correct order by giving them priorities.

Priorities apply to all kinds of scripts. This means that, for example, [synchronous and asynchronous scripts](types-of-script/index.md) don't have separate priority lists. They both join the same queue.

## How priority works

Scripts with **lower priority value** run **before** scripts with **higher values**.

TODO: VISUALIZATION

If scripts have the same priority, the order in which Stride runs them isn't deterministic. You might give scripts the same priority if you don't care which order they run in.

## Set a script priority

Priorities aren't set in the scripts themselves. Instead, they're set in the script component properties on the entity the script is attached to.

1. Attach the script to an entity. For information about how to do this, see [Use a script](use-a-script.md).

2. With the entity selected, in the **Property Grid**, set the **Priority** of that script that you want it to have.

    ![Set script priority](media/set-script-priority.png)

## See also

* [Types of script](types-of-script/index.md)
* [Create a script](create-a-script.md)
* [Use a script](use-a-script.md)
