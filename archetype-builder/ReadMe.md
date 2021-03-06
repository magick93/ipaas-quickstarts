## Archetype Builder

This code helps create archetypes from working projects without having to warp your project to make the archetype plugin happy.

It does this by keeping the [example projects](https://github.com/fabric8io/ipaas-quickstarts/tree/master/archetype-builder/src/test/examples) as stand alone examples folks can use, test and maintain directly; then it auto-generates the source of the [archetype projects](https://github.com/fabric8io/ipaas-quickstarts/tree/master/archetypes) via a build step.

The tool automatically copies the example projects source code to `src/main/resources/archetype-resources`.

So the directory `src/main/resources/archetype-resource` is included in the `.gitignore` so its never checked in.

To simplify things, the archetype projects have their own hand crafted root pom.xml files; you can also supply a default **archetype-metadata.xml** file in the root directory (which will be copied with the necessary required properties included). This means you can tweak whats included/excluded from the archetype and change the archetype pom.xml if need be; but keep the archetype data in sync with the working example program.

### Tips for archetype generation

In your example project, make sure you always specify the version of all dependencies and maven plugins. Feel free to use maven properties.

The tool removes the parent from the pom and extracts all the dynamic maven properties into required properties of the maven archetype, with default values from the current project.



