# gcloud-workload-identity


### Allow authentications from the Workload Identity Provider to impersonate the desired Service Account
gcloud iam service-accounts add-iam-policy-binding "my-service-account@${PROJECT_ID}.iam.gserviceaccount.com" \
  --project="${PROJECT_ID}" \
  --role="roles/iam.workloadIdentityUser" \
  --member="principalSet://iam.googleapis.com/projects/1234567890/locations/global/workloadIdentityPools/my-pool/attribute.repository/my-org/my-repo"

### Add the role iam.serviceAccountTokenCreator and if necessary also iam.serviceAccountUser 

gcloud iam service-accounts add-iam-policy-binding "$SERVICE_ACCOUNT@${PROJECT_ID}.iam.gserviceaccount.com" --project="${PROJECT_ID}" --role="roles/iam.serviceAccountTokenCreator" --member=serviceAccount:$SERVICE_ACCOUNT@${PROJECT_ID}.iam.gserviceaccount.com

example - 
  gcloud iam service-accounts add-iam-policy-binding "github-action@eternal-insight-403210.iam.gserviceaccount.com" \
--project="eternal-insight-403210" --role="roles/iam.serviceAccountTokenCreator" \
--member=serviceAccount:github-action@eternal-insight-403210.iam.gserviceaccount.com
