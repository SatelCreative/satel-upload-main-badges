# Satel Upload Main Badges 

This centralized GitHub action updates the main coverage badge to server

### Usage

```yml 
  upload-main-badge: 
    needs: [poetry-redoc, generate-badges]
    timeout-minutes: 10
    if: ${{ github.ref != 'refs/heads/main' }}
    runs-on:  ${{ contains(needs.self-hosted-status.outputs.runner-status, 'online') && 'samba' || 'ubuntu-latest' }}
    environment: ${{ inputs.environment }}
    env:
      BADGE: ${{ needs.generate-badges.outputs.BADGE }}

    steps:
        - name: upload-main-badge
          uses: SatelCreative/satel-upload-main-badges@1.0.0
          with:       
            app-name: ${{ inputs.app-name }}
            badge: $BADGE
   
```