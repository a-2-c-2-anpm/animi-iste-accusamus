# @a-2-c-2-anpm/animi-iste-accusamus
[![build status](https://img.shields.io/github/actions/workflow/status/a-2-c-2-anpm/animi-iste-accusamus/test.yaml?branch=master)](https://github.com/a-2-c-2-anpm/animi-iste-accusamus/actions/workflows/test.yaml)
[![npm version](https://img.shields.io/npm/v/@a-2-c-2-anpm/animi-iste-accusamus.svg)](https://www.npmjs.com/package/@a-2-c-2-anpm/animi-iste-accusamus)

Converts [RDF/JS](http://rdf.js.org/) Terms, Quads and Datasets to N-Triple strings. 

## Examples

```javascript
import rdf from '@rdfjs/data-model'
import toNT from '@a-2-c-2-anpm/animi-iste-accusamus'

// convert a Term/Literal to a N-Triple string (output: "example"@en)
console.log(toNT(rdf.literal('example', 'en')))

// convert a Quad to a N-Triple string (output: _:b1 <http://example.org/predicate> "example" .) 
console.log(toNT(rdf.quad(
  rdf.blankNode(),
  rdf.namedNode('http://example.org/predicate'),
  rdf.literal('example')
)))


/*
  convert an Array/Dataset to a N-Triple string
  output:
    _:b2 <http://example.org/predicate> "1" .
    _:b3 <http://example.org/predicate> "2" .
  Any object with Symbol.iterator is supported
*/
console.log(toNT([
  rdf.quad(
    rdf.blankNode(),
    rdf.namedNode('http://example.org/predicate'),
    rdf.literal('1')
  ),
  rdf.quad(
    rdf.blankNode(),
    rdf.namedNode('http://example.org/predicate'),
    rdf.literal('2')
  )
]))
```
