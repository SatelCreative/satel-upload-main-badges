# Satel Upload Main Badges 

This centralized GitHub action uploads the main coverage badges on the server

### Usage

```yml 
  upload-main-badge: 
    needs: [poetry-redoc, generate-badges]
    timeout-minutes: 10
    if: ${{ github.ref != 'refs/heads/main' }}
    runs-on: samba
    environment: ${{ inputs.environment }}
    env:
      BADGE: ${{ needs.generate-badges.outputs.BADGE }}
    steps:
        - name: upload-main-badge
          uses: SatelCreative/satel-upload-main-badges@1.0.0
          with:       
            app-name: ${{ inputs.app-name }}
            badge: "${{ env.BADGE }}"
   
```
