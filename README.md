# An examplary multi flavour app


This repo is an example of a multi-flavoured plugin app in the
[Arkitekt](https://arkitekt.live) framework.

As opposed to an app with just one flavour (the default vanilla)
this app can be build with different flavours, each of which
can have its own set of dependencies and will generate its own
docker image.

The flavours are defined in the `flavours` directory within the
app. Each flavour is a directory containing a `Dockerfile` and
a `config.yaml`, which defines selectors for the flavour.

Selectors are used to determine which flavour to use for a given
enviroment and hardware configuration. In this example app, we have
two flavours:

- Vanilla: The default flavour, which is used if no other flavour
  is selected, it has no selectors defined and will be used for
    all environments and hardware configurations, as a fallback.

- Cuda: A flavour which uses a base image with CUDA support and
  defines a selector defined as a "cuda" type selector, which can
  only be used on hardware with CUDA support.


Selectors are interpreted by the Port Service, which is part of
the Arkitekt framework. The Port Service is responsible for the
deployment of apps and will select the flavour to use based on
the selectors defined in the flavour's `config.yaml` and the
hardware configuration of the device the app is deployed to.

## Experimental

This feature is still experimental and may change in the future,
including the format of the `config.yaml` file and the way the
Port Service interprets selectors. To beta test this feature,
please install arkitekt cli version 0.7.0a0 or later.