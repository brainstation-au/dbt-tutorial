Welcome to your new dbt project!

### Project structure

This project has been created following the [getting started](https://docs.getdbt.com/tutorial/setting-up) instructions. It includes creations of credentials to execute the models in bigquery.

This project assumes you have created your gcp credentials following the above instructions and saved the JSON file in `$HOME/.gcp/`. The docker compose makes that credentials available within the container instance.

### Setting up profile

Please create a file `$HOME/.dbt/profiles.yml` with following content:
```yaml
dbt_tutorial: # this needs to match the profile: in your dbt_project.yml file
  target: dev
  outputs:
    dev:
      type: bigquery
      method: service-account
      keyfile: /root/.gcp/<credential-filename>.json
      project: <my-project-name>
      dataset: <dbt_my_name>
      threads: 1
      location: US
      timeout_seconds: 300
      priority: interactive
```

Please choose [a location](https://cloud.google.com/bigquery/docs/locations) that's appropriate for your situation.

### Using the starter project

Start `bash` in docker: `docker-compose run --rm sh`

Now you are ready to run any `dbt` [cli command](https://docs.getdbt.com/reference/dbt-commands).

Try running the following commands:
- dbt compile
- dbt run
- dbt test


### Resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](http://slack.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices
