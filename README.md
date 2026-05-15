# TinyFlags — opam (OCaml)

The opam port of TinyFlags. Built with `dune`; the Alcotest suite under
`test/test_tinyflags.ml` covers defaults, rollout boundaries, and variant
validation. Behavior, validation, and test-coverage requirements are shared
across every ecosystem — see [`../lib-spec.md`](../lib-spec.md).

## Package-native AXM recommendation

opam packages recommend extensions via `x-axm-<field>` custom fields directly
in the `.opam` file — there is no sidecar. opam preserves any field starting
with `x-` through publication to opam-repository:

```opam
x-axm-recommendedExtensions: ["@examples/packs/ocaml-opam-tinyflags@^0.1.0"]
```

`axm discover` reads this from
`~/.opam/<switch>/lib/agentxm-example-tinyflags/opam` in any consumer project.

## Commands

```bash
opam install . --deps-only --with-test
dune build
dune runtest
```

## Companion extensions

Sources live under [`.axm/extensions/@examples/`](.axm/extensions/@examples/)
and are marked authored in `.axm/settings.json`. The pack bundles the three
skills and the maintainer subagent.

| Type     | FQN                                                    | Homepage                                                                |
| -------- | ------------------------------------------------------ | ----------------------------------------------------------------------- |
| Skill    | `@examples/skills/ocaml-opam-tinyflags-add-flag`       | https://agentxm.ai/@examples/skills/ocaml-opam-tinyflags-add-flag       |
| Skill    | `@examples/skills/ocaml-opam-tinyflags-rollout-review` | https://agentxm.ai/@examples/skills/ocaml-opam-tinyflags-rollout-review |
| Skill    | `@examples/skills/ocaml-opam-tinyflags-cleanup-flag`   | https://agentxm.ai/@examples/skills/ocaml-opam-tinyflags-cleanup-flag   |
| Subagent | `@examples/subagents/ocaml-opam-tinyflags-maintainer`  | https://agentxm.ai/@examples/subagents/ocaml-opam-tinyflags-maintainer  |
| Pack     | `@examples/packs/ocaml-opam-tinyflags`                 | https://agentxm.ai/@examples/packs/ocaml-opam-tinyflags                 |

Each manifest declares `pkg:opam/agentxm-example-tinyflags` as a companion
package.

## Paired consumer

[`../ocaml-opam-app/`](../ocaml-opam-app/) — the `pawmatch` CLI that consumes
this library through realistic flag seams.
