# Python image dedupe (K8s)

This is extension of work done by [markusressel](https://github.com/markusressel/py-image-dedup).

This "should" work with any kubernetes setup, but mainly tested with "microk8s" in Arch Linux (Manjaro).

## Manifest layout

|Key|Value|Remarks|
|---|---|---|
|Namespace |`nullbr41n`| |
|App Image |`py-image-dedup:v2.0.1`| |
|Elasticsearch |`elasticsearch:7.9.0`| |
|Volume:HostPath|`/mnt/nas/media`| <CHANGE_ME> |
|PY_IMAGE_DEDUP_ANALYSIS_USE_EXIF_DATA|False| <CHANGE_ME> |

### Decisions

`Namespace`: Keeping close to author.

`App Image`: Latest version of dependency update has issue flagged [here](https://github.com/markusressel/py-image-dedup/issues/329).

`Elasticsearch`: Newish version as time of commit.

`Volume HostPath`: This needs changed to suit your need.

`PY_IMAGE_DEDUP_ANALYSIS_USE_EXIF_DATA`: This is false to make it work with `NAS` metadata signature that can generate noise.

### Usages

```
kubectl apply -f manifest
```

Note: Elasticsearch is used as backend and project is forked extension of [image-match](https://github.com/rhsimplex/image-match)
