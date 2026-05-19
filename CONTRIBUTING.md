# Contributing

Please ensure all code follows the conventions established in this project.

## Before Committing

Run the build to verify everything is working:

```bash
npm run build gm-starter [output-dir]
```

## Conventions

- The single platform adapter `platforms/skill.js` extends PlatformAdapter
- File generation logic goes in `createFileStructure()`
- Use TemplateBuilder methods for shared generation logic
- Skills are auto-discovered from gm-starter/skills/

## Testing

Build the gm-skill output:

```bash
node cli.js gm-starter /tmp/test-build
```
