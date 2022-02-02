---
title: Visual Studio için depo oluşturma
titleSuffix: ''
description: Git kullanarak Visual Studio bir depo oluşturun veya bir Azure DevOps depoya gidin.
ms.date: 02/02/2022
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 2125d832225918cc0118f689e74bacfdb7e08ee8
ms.sourcegitcommit: 23b0ef3815833426933ff6491271034658683f9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137983799"
---
# <a name="create-a-repo-in-visual-studio"></a>Visual Studio için depo oluşturma

Visual Studio, bir depoyu doğrudan ıde 'den klonlamanızı kolaylaştırır. Aşağıdaki adımları uygulayın:

## <a name="prerequisites"></a>Önkoşullar

Bu makaleyi izlemek için şunlar gerekir:
+ [Visual Studio yüklendi](../install/install-visual-studio.md)

+ [GitHub kullanıcı hesabı](git-create-github-account.md)

## <a name="create-a-github-repo"></a>GitHub deposu oluşturma

1. Visual Studio açın ve sonra **yeni proje oluştur**' u seçin.

    > [!TIP]
    > bir depoya eklemek için Visual Studio ' de zaten bir projeniz yoksa, hızlıca [yeni bir C# konsol uygulaması oluşturabilir](../get-started/csharp/tutorial-console.md#create-a-project) ve bunu **mynewapp** olarak adlandırın. Visual Studio yeni uygulamanızı varsayılan "*Hello, World!*" ile doldurur kodudur.

1. **Git** menüsünde **Git deposu oluştur**' u seçin.

    :::image type="content" source="media/vs-2022/git-menu-create-git-repository.png" alt-text="Visual Studio git menüsündeki git deposu oluşturma seçeneğinin ekran görüntüsü.":::

1. **Git deposu oluştur** iletişim kutusunda, **Yeni bir uzaktan gönder** bölümünde **GitHub**' yi seçin.

    :::image type="content" source="media/vs-2022/git-menu-create-github-repo-dialog.png" alt-text="git menüsünden git deposu oluşturma seçeneğinin ekran görüntüsü, GitHub seçimi vurgulanmış şekilde Visual Studio.":::

1. **Git deposu oluştur** iletişim kutusunun **yeni bir GitHub deposu oluştur** bölümünde, oluşturmak istediğiniz deponun adını girin.

    > [!TIP]
    > GitHub hesabınızda henüz oturum açmadıysanız, bu ekrandan de yapabilirsiniz.

1. Oturum açtıktan sonra depo bilgilerinizi girdikten sonra, deponuzu oluşturmak ve uygulamanızı eklemek için **Oluştur ve Gönder** düğmesini seçin.

    :::image type="content" source="media/vs-2022/git-menu-create-git-repo-push-code.png" alt-text="Git deposu oluştur penceresi kullanılarak girilen kullanıcının GitHub bilgisinin ekran görüntüsü.":::

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu aç

bir depoyu oluşturduktan veya [klonladıktan](git-clone-repository.md)sonra, Visual Studio git deposunu algılar ve git menüsündeki **yerel depolar** listenize ekler. Buradan git depolarınız arasında hızlı bir şekilde erişebilir ve geçiş yapabilirsiniz.

## <a name="create-an-azure-devops-repo"></a>Azure DevOps deposu oluşturma

1. Visual Studio açın ve sonra **yeni proje oluştur**' u seçin.

    > [!TIP]
    > bir depoya eklemek için Visual Studio ' de zaten bir projeniz yoksa, hızlıca [yeni bir C# konsol uygulaması oluşturabilir](../get-started/csharp/tutorial-console.md#create-a-project) ve bunu **mynewapp** olarak adlandırın. Visual Studio yeni uygulamanızı varsayılan "*Hello, World!*" ile doldurur kodudur.

1. **Git** menüsünde **Git deposu oluştur**' u seçin.

1. **Git deposu oluştur** iletişim kutusunda, **Yeni bir uzaktan gönder** bölümünde **Azure DevOps**' yi seçin.

1. **yeni bir Azure DevOps deposu oluştur** bölümünde Azure hesabınızda oturum açın ve sonra **Project** açılır listesinden bir proje seçin.

1. Depoyu oluşturmak ve uygulamanızı eklemek için **Oluştur ve Gönder** düğmesini seçin.

    :::image type="content" source="media/vs-2022/git-menu-publish-azure-devops.png" alt-text="Bir git deposu oluştur iletişim kutusunun oluşturma ve gönderme işlevinin, tek bir eylemle kod yayımlamak için kullanabileceğiniz ekran görüntüsü.":::

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğa devam etmek için [dal oluştur](git-create-branch.md) sayfasını ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: bir depodan bir proje açın](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md)
- [Visual Studio oturum açın](../ide/signing-in-to-visual-studio.md)
- [Visual Studio & GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
