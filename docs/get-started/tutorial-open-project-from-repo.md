---
title: 'Öğretici: bir depodan bir proje açın'
description: Visual Studio 'Yu kullanarak bir git veya Azure DevOps deposunda bir projeyi açmayı öğrenin.
ms.custom: get-started
ms.date: 11/10/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 91fb06a50fe0c992d3018aee31cfc963544f8b97
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436087"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: bir depodan bir proje açın

Bu öğreticide, bir depoya ilk kez bağlanmak ve ardından bir projeyi açmak için Visual Studio kullanacaksınız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>GitHub deposundan proje açma

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda, **File** > **Open** > **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini-Connect** bölmesi açılır.

    ![Visual Studio IDE içinde Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. **Yerel Git depoları** bölümünde, **Kopyala** ' yı seçin.

    ![Yerel Git depoları bölümünden kopyayı seçin](./media/open-proj-repo-local-git-repo-clone.png)

1. **_Kopyalanacak bir git deposunun URL 'sini girin_*_, deponuzu URL 'sini yazın veya yapıştırın ve ardından _ ENTER tuşuna basın***. (GitHub 'da oturum açmak için bir istem alabilirsiniz; varsa, bunu yapın.)

   Visual Studio deponuzu klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

   ![Çözüm Gezgini "çözümler ve klasörler" i seçin](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. Bunu seçin ve Visual Studio çözümünüzü açar.

   ![Çözüm Gezgini açılır listesinden neleri açmak istediğinizi seçin](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

   ![Visual Studio kullanarak GitHub deposunda proje açma animasyonu](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 ' de yeni tümleşik git deneyimini denemek istiyorsanız, [**16,8 sürümüne**](/visualstudio/releases/2019/release-notes/)güncelleştirdiğinizden emin olun. Daha fazla bilgi için bkz. [Visual Studio 'Da yeni git deneyimi](../ide/git-with-visual-studio.md) sayfası.

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde, **Kopyala veya kullanıma alma kodu** ' nu seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından **Kopyala** ' yı seçin.

   ![' Kopya veya kullanıma alma kodu ' penceresini görüntüleyin](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio, projeden projeyi açar.

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. Bunu seçin ve Visual Studio çözümünüzü açar.

   ![Çözüm Gezgini açılır listesinden neleri açmak istediğinizi seçin](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Azure DevOps deposundan bir proje açma

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda, **File** > **Open** > **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini-Connect** bölmesi açılır.

    ![Visual Studio IDE içinde Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. Azure DevOps deponuza bağlanmanın iki yolu aşağıda verilmiştir:

      - **Barındırılan hizmet sağlayıcıları** bölümünde **Bağlan...** seçeneğini belirleyin.

        ![Visual Studio IDE içinde Takım Gezgini penceresinin barındırılan hizmet sağlayıcıları bölümü](./media/open-proj-repo-azure-devops.png)

      - **Bağlantıları Yönet** açılan listesinde, **bir projeye Bağlan...** seçeneğini belirleyin.

        ![Visual Studio IDE içinde Takım Gezgini penceresinin bağlantıları yönetme bölümü](./media/open-proj-repo-azuredevops-manage-connections.png)

1. **Bir projeye Bağlan** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **Kopyala** ' yı seçin.

      ![Visual Studio 'dan oluşturulan "projeye Bağlan" iletişim kutusu](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda gördükleriniz, erişiminiz olan Azure DevOps depolarına bağlıdır.

1. Visual Studio deponuzu klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

      ![Visual Studio 'daki Takım Gezgini "çözümler ve klasörler" bildirimi](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve klasörler" açılan menüsünde bir çözüm dosyası (özellikle bir. sln dosyası) görüntülenir. Bunu seçin ve Visual Studio çözümünüzü açar.

   Deponuzda bir çözüm dosyanız yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde, **Kopyala veya kullanıma alma kodu** ' nu seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **Bir depoya Gözatatıon** bölümünde **Azure DevOps** ' u seçin.

   ![' Kodu kopyala veya kullanıma alma ' penceresini görüntüle](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bir projeye Bağlan** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **Kopyala** ' yı seçin.

      ![Visual Studio 'dan oluşturulan "projeye Bağlan" iletişim kutusu](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda gördükleriniz, erişiminiz olan Azure DevOps depolarına bağlıdır.

   Visual Studio **Takım Gezgini** açar ve kopya tamamlandığında bir bildirim görüntülenir.

     ![Klondan sonra Visual Studio 'daki Takım Gezgini penceresi tamamlanmıştır](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için **klasör görünümünü göster** bağlantısını seçin.

     ![Klondan sonra Visual Studio 'daki Takım Gezgini penceresinin çözümler bölümü tamamlanmıştır](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **Çözüm Gezgini** açar.

1. Açmak için bir çözüm dosyası (özellikle bir. sln dosyası) aramak üzere **çözümler ve klasörler** bağlantısını seçin.

      ![Visual Studio 'daki Takım Gezgini "çözümler ve klasörler" bildirimi](./media/open-proj-repo-solutions-folders.png)

   Deponuzda bir çözüm dosyanız yoksa, "hiçbir çözüm bulunamadı" iletisi görüntülenir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ile kod oluşturmaya hazırsanız, dile özgü aşağıdaki öğreticilerden birine gidin:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript** , **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="vs-2017"

- [Azure DevOps Services: Azure Repos ve Visual Studio ile çalışmaya başlama](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Azure DevOps ile çalışmaya başlama](/learn/modules/get-started-with-devops/)
- [Visual Studio 2019 'de yeni git deneyimi](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio 'da yeni git deneyimi](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Azure Repos ve Visual Studio ile çalışmaya başlama](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Azure DevOps ile çalışmaya başlama](/learn/modules/get-started-with-devops/)

::: moniker-end
