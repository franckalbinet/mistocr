# Release notes

<!-- do not remove -->

## 0.7.0

### Breaking Changes

- Replace lisette with fastllm; heading-fix functions are now async ([#2](https://github.com/franckalbinet/mistocr/issues/2))

### Bugs Squashed

- Heading fixes send ANTHROPIC_API_KEY to every provider ([#3](https://github.com/franckalbinet/mistocr/issues/3))


## 0.6.0

### Breaking Changes

- Require mistralai>=2 and import Mistral from mistralai.client ([#1](https://github.com/franckalbinet/mistocr/issues/1))


## 0.2.1
First working version of the full pipeline: batch OCR -> fixing markdown headings -> describing images and injecting those description in markdown
