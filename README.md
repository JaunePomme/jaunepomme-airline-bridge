Deployed at : 
https://jaunepomme-airline-bridge.vercel.app

I added my own warp route Arbitrum-Base with Weth on it.

Récap des modifs apportées pour faire tourner le bousin et déployer :
-ajout du .env et de la valeur du projetId: Faut la récupérer sur leur lien walletconnect cloud là, tu crées un projet, appkit/NextJs, ok, et après en bas du dashboard tu cliques sur un truc et tu verras y te montre un exemple du fichier avec ton projetID dedans, récupère et mets le dans ton .env
-Commenter la lib de jmrossy là pour accéder au jazzicon. Si besoin cloner le repo et c/c le code dans ce repo directement.. mais flm j'ai juste commenté. ça marche en local mais en déploiement l'accès au repo machait pas via ssh. J'ai mis en place ma clé ssh sur vercel pck vercel doit pull ce repo mais ça bugguait fort donc j'ai fini par le commenter ce truc inutile (c'est juste une icone ptain)
-Commenter le backpackwallet, jsais pas la lib marchait pas, j'ai pas marché j'ai commenté
-npm install -g yarn parceque je l'avais pas et lancer du coup un yarn install une fois fait.
-Peut-être dans le package-lock.json y'a du jmrossy machin icon qui traine, bien le supprimer.
-Au niveau du linter, y'a un souci du status===status.failed, juste remplacer par la constante isFailed.
-npm run dev, yarn install, yarn lint, si ces 3 marchent, ça devrait être bon, go déployer sur vercel gratos, faut un compte github évidemment.

# Hyperlane Warp Route UI Template

This repo contains an example web interface for interchain tokens built with [Hyperlane Warp Route](https://docs.hyperlane.xyz/docs/reference/applications/warp-routes). Warp is a framework to permisionlessly bridge tokens to any chain.

## Architecture

This app is built with Next & React, Wagmi, RainbowKit, and the Hyperlane SDK.

- Constants that you may want to change are in `./src/consts/`, see the following Customization section for details.
- The index page is located at `./src/pages/index.tsx`
- The primary features are implemented in `./src/features/`

## Customization

See [CUSTOMIZE.md](./CUSTOMIZE.md) for details about adjusting the tokens and branding of this app.

## Development

### Setup

#### Build
```sh
# Install dependencies
yarn

# Build Next project
yarn build
```

#### Configure

You need a `projectId` from the WalletConnect Cloud to run the Hyperlane Warp Route UI successfully. 
Sign up to [WalletConnect Cloud](https://cloud.walletconnect.com/), create 
new project with AppKit and Next.js and copy the `projectId` from there.

### Run

You can add `.env.local` file next to `.env.example` where you set `projectId` copied from WalletConnect Cloud.
```sh
# Start the Next dev server
yarn dev
```

Or you can set the WalletConnect Cloud `projectId` to use as follows:
```
NEXT_PUBLIC_WALLET_CONNECT_ID=<projectId> yarn dev
```

### Test

```sh
# Lint check code
yarn lint

# Check code types
yarn typecheck
```

### Format

```sh
# Format code using Prettier
yarn prettier
```

### Clean / Reset

```sh
# Delete build artifacts to start fresh 
yarn clean
```

## Deployment

The easiest hosting solution for this Next.JS app is to create a project on Vercel.

## Learn more

For more information, see the [Hyperlane documentation](https://docs.hyperlane.xyz/docs/reference/applications/warp-routes).
