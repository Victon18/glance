# common folder
1. make a new folder with common and install and setup node,zod and typescript
```ts
export const signupInput = z.ooject({
  username = z.string(),
  password = z.string(),
})
export type SignUpParams = z.infer<typeof signupInput>
```
2. now both frontend and backend can import it
# npm
1.
```bash
# login into npm
npm login
```
2. edit package.json
```json
{
  "name":"unique name",
  "version": "change every push",
  "main":"dist/index.json",
}
```
3. publish the file
```bash
npm pack
npm publish --access=publish
```
4. create a .npmignore file
5. create declaration files => change tsconfig to "declaration" = true,
# turborepo
```bash
# initialization
npx create-turbo@latest
# Select npm workspaces as the monorepo framework
```
### structure
1. End user apps (websites/core backend)
  - apps/web - A Next.js website
  - apps/docs - A Docs website that has all the documentation related to your project
2. Helper packages
  - packages/ui - UI packages
  - packages/typescript-config - Shareable TS configuration
  - packages/eslint-config - Shareable ESLine configuration
