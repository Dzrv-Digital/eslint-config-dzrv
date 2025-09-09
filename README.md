**🚀 Enterprise-grade reusable ESLint configuration for modern JavaScript/TypeScript projects with React support, security rules, and Prettier integration.**

## Features
- ✅ **Modern ESLint v9** with flat config support
- ✅ **TypeScript** ready with latest @typescript-eslint rules
- ✅ **React & JSX** support with accessibility rules
- ✅ **Import organization** with automatic sorting
- ✅ **Unused imports removal** 
- ✅ **Security rules** to catch common vulnerabilities
- ✅ **Code quality** rules for maintainable code
- ✅ **Prettier integration** for consistent formatting
- ✅ **Self-closing JSX tags** and React best practices
- ✅ **Airbnb-inspired** rule set with modern updates

## Installation
```
npm install --save-dev eslint-config-dzrv eslint typescript
```

### Peer Dependencies
Make sure you have these installed:
```
npm install --save-dev eslint@^9.0.0 typescript@>=4.7.0
```

## Usage
#### Basic JavaScript Project
```
// eslint.config.js
import dzrvConfig from 'eslint-config-dzrv';
export default [
  ...dzrvConfig.configs.recommended,
  {
    // Your custom overrides
  },
];
```

#### TypeScript Project
```
// eslint.config.js
import dzrvConfig from 'eslint-config-dzrv';

export default [
  ...dzrvConfig.configs['recommended-typescript'],
  {
    // Your custom overrides
  },
];
```

#### React Project
```
// eslint.config.js
import dzrvConfig from 'eslint-config-dzrv';

export default [
  ...dzrvConfig.configs['recommended-react'],
  {
    // Your custom overrides
  },
];
```

#### TypeScript + React Project (Full Stack)
```
// eslint.config.js
import dzrvConfig from 'eslint-config-dzrv';

export default [
  ...dzrvConfig.configs['recommended-typescript-react'],
  {
    // Your custom overrides
    rules: {
      // Override any rules as needed
      'no-console': 'off',
      '@typescript-eslint/no-explicit-any': 'error',
    },
  },
];
```

## Available Configurations
| Config | Description |
|--------|-------------|
| `recommended` | Base JavaScript rules + Prettier |
| `recommended-typescript` | Base + TypeScript rules + Prettier |
| `recommended-react` | Base + React/JSX rules + Prettier |
| `recommended-typescript-react` | All rules combined (Full stack) |

## Individual Configs
You can also use individual configurations:

```javascript
import dzrvConfig from 'eslint-config-dzrv';

export default [
  dzrvConfig.configs.base,           // Core JavaScript rules
  dzrvConfig.configs.typescript,     // TypeScript-specific rules
  dzrvConfig.configs.react,         // React-specific rules  
  dzrvConfig.configs.prettier,      // Prettier integration
];
```

## Key Rules Included

### Code Quality
- Complexity limits (max 10)
- Function length limits (50 lines)
- Parameter limits (4 max)
- Consistent return statements
- No magic numbers
- Prefer modern JS features

### Import Management
- Automatic import ordering and grouping
- Unused import removal
- No circular dependencies
- Consistent file extensions

### TypeScript
- Strict type checking
- Consistent type imports
- No unnecessary type assertions
- Prefer modern TS features
- Interface over type aliases

### React
- Self-closing components
- JSX best practices
- React Hooks rules
- Accessibility (a11y) rules
- No array indices as keys

### Security
- Detect unsafe regex
- Prevent object injection
- Buffer security
- Eval detection
- Timing attack prevention

## Prettier Integration

This config works seamlessly with Prettier. Create a `.prettierrc` file:

```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false
}
```

## Customization

### Override Rules

```javascript
// eslint.config.js
import dzrvConfig from 'eslint-config-dzrv';

export default [
  ...dzrvConfig.configs['recommended-typescript-react'],
  {
    rules: {
      // Make console.log an error in production
      'no-console': 'error',
      
      // Allow any types in some cases
      '@typescript-eslint/no-explicit-any': 'warn',
      
      // Customize import order
      'import/order': ['error', {
        'newlines-between': 'never',
      }],
    },
  },
];
```

### Ignore Files

```javascript
// eslint.config.js
export default [
  ...dzrvConfig.configs['recommended-typescript-react'],
  {
    ignores: [
      'dist/**',
      'build/**', 
      'coverage/**',
      '*.config.js',
    ],
  },
];
```

### Environment-Specific Rules

```javascript
// eslint.config.js
export default [
  ...dzrvConfig.configs['recommended-typescript-react'],
  
  // Development files
  {
    files: ['**/*.dev.ts', '**/*.test.ts', '**/*.spec.ts'],
    rules: {
      'no-console': 'off',
      'no-debugger': 'warn',
    },
  },
  
  // Production builds
  {
    files: ['src/**/*.ts'],
    rules: {
      'no-console': 'error',
      'no-debugger': 'error',
    },
  },
];
```

## Migration from Legacy ESLint Configs

### From Airbnb Config

```javascript
// Before (ESLint v8)
module.exports = {
  extends: ['airbnb', 'airbnb-typescript'],
  // ...
};

// After (ESLint v9)
import dzrvConfig from 'eslint-config-dzrv';

export default [
  ...dzrvConfig.configs['recommended-typescript-react'],
];
```

### From Create React App

```javascript
// Replace react-scripts eslint config
import dzrvConfig from 'eslint-config-dzrv';

export default [
  ...dzrvConfig.configs['recommended-typescript-react'],
  {
    rules: {
      // CRA allows console in development
      'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'warn',
    },
  },
];
```

## Package Scripts

Add these to your `package.json`:

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix",
    "lint:check": "eslint . --max-warnings 0"
  }
}
```

## IDE Integration

### VS Code

Install the ESLint extension and add to your settings:

```json
{
  "eslint.experimental.useFlatConfig": true,
  "eslint.format.enable": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

## License

MIT © [Dzrv Digital](https://github.com/dzrv-digital)