---
title: Gerenciar o nome de branch-padrão para repositórios na sua organização
intro: 'Você pode definir o nome do branch-padrão para repositórios que os integrantes criam na sua organização em {% data variables.product.product_location %}.'
redirect_from:
  - /github/setting-up-and-managing-organizations-and-teams/managing-the-default-branch-name-for-repositories-in-your-organization
permissions: Organization owners can manage the default branch name for new repositories in the organization.
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Organizations
  - Teams
shortTitle: Gerenciar nome do branch padrão
---

## Sobre o gerenciamento do nome do brancc-padrão

Quando um integrante da sua organização cria um novo repositório na sua organização, o repositório contém um branch, que é o branch-padrão. Você pode alterar o nome que {% data variables.product.product_name %} usa para o branch-padrão em novos repositórios que os integrantes da sua organização criam. Para obter mais informações sobre o branch padrão, consulte "[Sobre branches](/github/collaborating-with-issues-and-pull-requests/about-branches#about-the-default-branch)".

{% data reusables.branches.change-default-branch %}

Se um proprietário da empresa tiver aplicado uma política para o nome do branch padrão para sua empresa, você não poderá definir um nome do branch padrão para sua organização. Em vez disso, você pode alterar o branch padrão para repositórios individuais. For more information, see {% ifversion fpt %}"[Enforcing repository management policies in your enterprise](/enterprise-cloud@latest/admin/policies/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-the-default-branch-name)"{% else %}"[Enforcing repository management policies in your enterprise](/admin/policies/enforcing-repository-management-policies-in-your-enterprise#enforcing-a-policy-for-the-default-branch-name)"{% endif %} and "[Changing the default branch](/github/administering-a-repository/changing-the-default-branch)."

## Definir o nome do branch-padrão

{% data reusables.profile.access_org %}
{% data reusables.profile.org_settings %}
{% data reusables.organizations.repository-defaults %}
3. Em "Branch padrão do repositório", clique em **Alterar o nome do branch-padrão agora**. ![Botão de sobrescrever](/assets/images/help/organizations/repo-default-name-button.png)
4. Digite o nome-padrão que você gostaria de usar para novos branches. ![Caixa de texto para digitar o nome-padrão](/assets/images/help/organizations/repo-default-name-text.png)
5. Clique em **Atualizar**. ![Botão de atualizar](/assets/images/help/organizations/repo-default-name-update.png)

## Leia mais

- "[Gerenciar o nome do branch-padrão para seus repositórios](/github/setting-up-and-managing-your-github-user-account/managing-the-default-branch-name-for-your-repositories)"
