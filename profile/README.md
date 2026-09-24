<p align="center">
  <a href="https://datarobot.com">
    <img src="https://af.datarobot.com/img/datarobot_logo.avif" width="600px" alt="DataRobot Logo"/>
  </a>
</p>
<h2 align="center">DataRobot Labs</h2>
<p align="center">
  <a href="https://datarobot.com">Homepage</a>
  ·
  <a href="https://docs.datarobot.com">Documentation</a>
  ·
  <a href="https://af.datarobot.com">App Framework Docs</a>
  ·
  <a href="https://docs.datarobot.com/en/docs/get-started/troubleshooting/general-help.html">Support</a>
</p>

## DataRobot Solutions Labs

Welcome to the workbench. 🧪

**Solutions Labs** builds with customers and partners on the newest parts of the DataRobot platform — agentic applications, new runtimes, integrations that nobody has wired together yet. We take the platform where it hasn't been taken before, find out what breaks, and turn the parts worth keeping into something anyone can reuse.

If [datarobot.com](https://datarobot.com) is the showroom, this is the garage.

> **Disclaimer:** work in this organization is experimental by design. It is provided as-is, with no official support, and it is not part of the DataRobot product. For supported functionality, start at [docs.datarobot.com](https://docs.datarobot.com).

## What we do

| | |
| --- | --- |
| 🤝 **Partner and customer builds** | Applications built alongside the people who will run them, on platform capabilities that are new enough to still have sharp edges. |
| 🧰 **Reusable assets** | The patterns that survive more than one engagement get rewritten as components, templates, and libraries, then published where everyone can find them. |
| 🛠️ **Day-zero experiments** | We pick up brand-new platform features before customers reach them, and send the findings back to the teams that build them. |
| 📓 **Field notes** | What actually happened when the demo met production. |

Most of what we produce doesn't stay here. Durable work graduates into [datarobot-oss](https://github.com/datarobot-oss) and [datarobot-community](https://github.com/datarobot-community), where it's maintained alongside the rest of DataRobot's open source. This organization holds the experiments themselves.

## DataRobot on GitHub

DataRobot's code is spread across several GitHub organizations. Which one you want depends on what you're doing:

| Organization | What lives there |
| --- | --- |
| [**datarobot**](https://github.com/datarobot) | DataRobot, Inc.'s primary organization. Home of our flagship public projects — [datarobot-user-models](https://github.com/datarobot/datarobot-user-models) (DRUM, the custom model runtime), [syftr](https://github.com/datarobot/syftr) (agentic workflow optimizer), and [dr-apps](https://github.com/datarobot/dr-apps) (host custom apps without building an image). |
| [**datarobot-oss**](https://github.com/datarobot-oss) | First-party open source from our R&D and customer-facing teams: the [`dr` CLI](https://github.com/datarobot-oss/cli), agent and GenAI runtime libraries, Terraform modules, GitHub Actions, and application templates. |
| [**datarobot-community**](https://github.com/datarobot-community) | Community-facing building blocks: [Foundational AI Application Templates](https://docs.datarobot.com/en/docs/workbench/wb-apps/app-templates/index.html), the [App Framework](https://af.datarobot.com) and its `af-component-*` modules, and the declarative API ([Pulumi](https://github.com/datarobot-community/pulumi-datarobot) / [Terraform](https://github.com/datarobot-community/terraform-provider-datarobot) providers). |
| [**datarobot-labs**](https://github.com/datarobot-labs) | 📍 *You are here.* Experiments, prototypes, and engagement work from Solutions Labs. Newest org, highest variance. |
| [**datarobot-forks**](https://github.com/datarobot-forks) | Forks of third-party open source we depend on, where we stage changes to send upstream. Nothing here is DataRobot-developed or supported. |

## Where to start

This organization is new and deliberately thin. If you arrived looking for something to build on, you almost certainly want one of these instead:

| If you want to… | Go here |
| --- | --- |
| Scaffold, run, and deploy a DataRobot app from your terminal | [`cli`](https://github.com/datarobot-oss/cli) — the `dr` CLI |
| Build an agentic application | [App Framework](https://af.datarobot.com) · [`datarobot-genai`](https://github.com/datarobot-oss/datarobot-genai) |
| Give your coding agent DataRobot skills | [`datarobot-agent-skills`](https://github.com/datarobot-oss/datarobot-agent-skills) |
| Start from a working application template | [Application templates](https://github.com/datarobot-community) |
| Stand up the infrastructure DataRobot runs on | [AWS](https://github.com/datarobot-oss/terraform-aws-dr-infra) · [Azure](https://github.com/datarobot-oss/terraform-azurerm-dr-infra) · [Google Cloud](https://github.com/datarobot-oss/terraform-google-dr-infra) |

## Get involved

- 💬 Join the conversation in [`#all-datarobot-community`](https://join.slack.com/t/datarobot-community/shared_invite/zt-3uzfp8k50-SUdMqeux25ok9_5wr4okrg) on Slack.
- 🐛 Found a bug or have an idea? Open an issue on the repository in question.
- 📚 Product documentation lives at [docs.datarobot.com](https://docs.datarobot.com); App Framework documentation at [af.datarobot.com](https://af.datarobot.com).
