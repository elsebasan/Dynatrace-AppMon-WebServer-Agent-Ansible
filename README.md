# Dynatrace-WebServer-Agent-Ansible

This Ansible role installs and configures the Dynatrace AppMon WebServer Agent of the [Dynatrace AppMon](https://www.dynatrace.com/support/doc/appmon/) solution.

**Note**: this role merely makes the Dynatrace AppMon WebServer Agent available, but it does not configure your web server to actually load it. See the [Dynatrace-Apache-HTTPServer-Agent-Ansible](https://github.com/dynaTrace/Dynatrace-Apache-HTTPServer-Agent-Ansible) role for an example that does.

## Download

The role is available via:

- [Ansible Galaxy](https://galaxy.ansible.com/Dynatrace/Dynatrace-WebServer-Agent)
- [GitHub](https://github.com/Dynatrace/Dynatrace-WebServer-Agent-Ansible)

## Requirements

This role downloads and installs the most recent version of the Dynatrace AppMon Web Server Agent from [http://downloads.dynatracesaas.com](http://downloads.dynatracesaas.com). Alternatively, you can place the installer artifact as `dynatrace-wsagent-linux-x64.tar` in the role's `files` directory from where it will be picked up during the installation. The default file name and URL can be overridden via the `dynatrace_wsagent_linux_installer_file_name` and `dynatrace_wsagent_linux_installer_file_url` attributes, respectively. Please refer to `defaults/main.yml` for a list of supported attributes.

## Role Variables

As defined in ```defaults/main.yml```:

| Name                                          | Default                                                                | Description |
|-----------------------------------------------|------------------------------------------------------------------------|-------------|
| *dynatrace_wsagent_linux_install_dir*         | /opt                                                                   | The Dynatrace AppMon Web Server Agent will be installed into the directory *$dynatrace_wsagent_linux_install_dir*/dynatrace-*$major*-*$minor*-*$rev*, where *$major*, *$minor* and *$rev* are given by the installer. A symbolic link to the actual installation directory will be created in *$dynatrace_wsagent_linux_install_dir*/dynatrace. |
| *dynatrace_wsagent_linux_installer_file_name* | dynatrace-wsagent-7.0.0.2449-linux-x86-64.tar                          | The file name of the Dynatrace AppMon Web Server Agent installer in the role's ```files``` directory. |
| *dynatrace_wsagent_linux_installer_file_url*  | https://files.dynatrace.com/downloads/OnPrem/dynaTrace/7.0/7.0.0.2449/dynatrace-wsagent-7.0.0.2449-linux-x86-64.tar | A HTTP, HTTPS or FTP URL to the Dynatrace AppMon Web Server Agent installer in the form (http\|https\|ftp)://[user[:pass]]@host.domain[:port]/path. |
| *dynatrace_wsagent_name*                      | dtwsagent                                                              | The name the Web Server Agent as it appears in Dynatrace AppMon. |
| *dynatrace_wsagent_collector_hostname*        | localhost                                                              | The location of the Collector the Web Server Agent shall connect to. |
| *dynatrace_wsagent_collector_port*            | 9998                                                                   | The port on the Collector the Web Server Agent shall connect to. |
| *dynatrace_wsagent_owner*                     | dynatrace                                                              | The system user that owns the Dynatrace AppMon installation.
| *dynatrace_wsagent_group*                     | dynatrace                                                              | The system user's group that owns the Dynatrace AppMon installation.
| *dynatrace_wsagent_role_name*                 | Dynatrace.Dynatrace-WebServer-Agent                                    | The actual name of this role in an [Ansible Playbook's](http://docs.ansible.com/playbooks.html) ```roles``` directory. |

## Example Playbook

```
- hosts: all
  roles:
    - role: Dynatrace.Dynatrace-WebServer-Agent
```

## Testing

We use [Test Kitchen](http://kitchen.ci) to automatically test our automated deployments with [Serverspec](http://serverspec.org) and [RSpec](http://rspec.info/):

1) Install Test Kitchen and its dependencies from within the project's directory:

```
gem install bundler
bundle install
```

2) Run all tests

```
kitchen test
```

By default, we run our tests inside [Docker](https://www.docker.com/) containers as this considerably speeds up testing time (see `.kitchen.yml`).

## Additional Resources

### Blogs

- [How to Automate Enterprise Application Monitoring with Ansible](http://apmblog.dynatrace.com/2015/03/04/how-to-automate-enterprise-application-monitoring-with-ansible/)
- [How to Automate Enterprise Application Monitoring with Ansible - Part II](http://apmblog.dynatrace.com/2015/04/23/how-to-automate-enterprise-application-monitoring-with-ansible-part-ii/)

### Presentations

- [Automated Deployments (of Dynatrace AppMon) with Ansible](http://www.slideshare.net/MartinEtmajer/automated-deployments-with-ansible)
- [Test-Driven Infrastructure with Ansible, Test Kitchen, Serverspec and RSpec](http://www.slideshare.net/MartinEtmajer/testing-ansible-roles-with-test-kitchen-serverspec-and-rspec-48185017)

## Problems? Questions? Suggestions?

This offering is [Dynatrace Community Supported](https://community.dynatrace.com/community/display/DL/Support+Levels#SupportLevels-Communitysupported/NotSupportedbyDynatrace(providedbyacommunitymember)). Feel free to share any problems, questions and suggestions with your peers on the Dynatrace Community's [Application Monitoring & UEM Forum](https://answers.dynatrace.com/spaces/146/index.html).

## License

Licensed under the MIT License. See the LICENSE file for details.
[![analytics](https://www.google-analytics.com/collect?v=1&t=pageview&_s=1&dl=https%3A%2F%2Fgithub.com%2FdynaTrace&dp=%2FDynatrace-WebServer-Agent-Ansible&dt=Dynatrace-WebServer-Agent-Ansible&_u=Dynatrace~&cid=github.com%2FdynaTrace&tid=UA-54510554-5&aip=1)]()
