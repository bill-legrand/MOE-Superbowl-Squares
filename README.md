# MOE Super Bowl Squares

A Super Bowl Squares pool application for Men of Emanuel.

## Features

- 10x10 grid with random number assignment
- Live score integration with ESPN API
- Quarter-by-quarter winner tracking
- Participant color coding
- Admin controls for shuffling and locking
- Responsive design

## Deployment

This app is deployed on Vercel. To deploy your own version:

1. Install Vercel CLI (optional):
   ```bash
   npm i -g vercel
   ```

2. Deploy using Vercel CLI:
   ```bash
   vercel
   ```

3. Or deploy via Vercel Dashboard:
   - Go to [vercel.com](https://vercel.com)
   - Import this project
   - Deploy

## Local Development

Simply open `index.html` in a web browser. No build process required.

## Configuration

Edit the `CONFIG` object in `index.html` to customize:
- Team names and abbreviations
- Price per square
- Random seed
- Quarter payouts
- API polling interval

## Super Bowl LX

- **Teams**: New England Patriots vs Seattle Seahawks
- **Date**: Sunday, February 8, 2026
- **Location**: Levi's Stadium, Santa Clara, CA
