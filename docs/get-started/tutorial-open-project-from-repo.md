---
title: 'Öğretici: Bir repodan proje açma'
description: Visual Studio'yu kullanarak Git veya Azure DevOps deposunda projeyi nasıl açacağınızı öğrenin.
ms.custom: get-started
ms.date: 03/30/2019
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
ms.openlocfilehash: 3af54d663cee1ad2b2dd4e8241678b88c635d376
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180431"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: Bir repodan proje açma

Bu öğreticide, visual studio'yu kullanarak ilk kez bir depoya bağlanır ve ondan bir proje açarsınız.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>GitHub reposundan proje açma

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan **Kaynak Denetimi'nden** **Dosya** > **Aç'ı** > seçin.

   **Takım Gezgini - Bağlan** bölmesi açılır.

    ![Visual Studio IDE içindeki Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. Yerel **Git Depoları** bölümünde **Klon'u**seçin.

    ![Yerel Git Depoları bölümünden Klon'u seçin](./media/open-proj-repo-local-git-repo-clone.png)

1. ***Klonlamak için Git repo'nun URL'sini girin,*** repo'nuz için URL'yi yazın veya yapıştırın ve ardından **Enter**tuşuna basın diyor. (GitHub'da oturum açmanız için bir istem alabilirsiniz; eğer öyleyse, bunu yapın.)

   Visual Studio repo'nuzu klonladıktan sonra Team Explorer kapanır ve Solution Explorer açılır. Çözümler listesini görüntülemek *için yukarıdaki Çözümler ve Klasörler'e tıklayın*diyen bir ileti görüntülenir. **Çözümleri ve Klasörleri**seçin.

   ![Çözüm Gezgini'nden "Çözümler ve Klasörler" seçeneğini belirleyin](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, "Çözümler ve Klasörler" fly-out menüsünde görünür. Seçin ve Visual Studio çözümünüzü açar.

   ![Çözüm Gezgini açılır listesinden ne açmak istediğinizi seçin](./media/open-proj-repo-github-solutions-folders-picker.png)

   Repo'nuzda bir çözüm dosyanız (özellikle .sln dosyası) yoksa, çıkış menüsünde "Çözüm Bulunamadı" yazar. Ancak, Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyayı çift tıklatabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız çalışmayı denetlemek için aşağıdaki animasyonu görüntüleyin.

   ![Visual Studio kullanarak GitHub repo'da proje açmaanimasyonu](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç **penceresinde, Klon'u**seçin veya kodu kullanıma çekin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından **Klon'u**seçin.

   !['Klon veya ödeme kodu' penceresini görüntüleme](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio repo'dan projeyi açar.

1. Kullanılabilir bir çözüm dosyanız varsa, "Çözümler ve Klasörler" fly-out menüsünde görünür. Seçin ve Visual Studio çözümünüzü açar.

   ![Çözüm Gezgini açılır listesinden ne açmak istediğinizi seçin](./media/open-proj-repo-github-solutions-folders-picker.png)

   Repo'nuzda bir çözüm dosyanız (özellikle .sln dosyası) yoksa, çıkış menüsünde "Çözüm Bulunamadı" yazar. Ancak, Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyayı çift tıklatabilirsiniz.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Azure DevOps reposundan proje açma

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan **Kaynak Denetimi'nden** **Dosya** > **Aç'ı** > seçin.

   **Takım Gezgini - Bağlan** bölmesi açılır.

    ![Visual Studio IDE içindeki Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. Azure DevOps repo'nuza bağlanmanın iki yolu şunlardır:

      - **Barındırılan Servis Sağlayıcıları** bölümünde **Bağlan...** seçeneğini belirleyin.

        ![Visual Studio IDE içindeki Team Explorer penceresinin Barındırılan Servis Sağlayıcıları bölümü](./media/open-proj-repo-azure-devops.png)

      - Bağlantıları **Yönet** açılır listesinde Projeye **Bağlan'ı seçin...**

        ![Visual Studio IDE içindeki Ekip Gezgini penceresinin Bağlantıları Yönet bölümü](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Projeye **Bağlan** iletişim kutusunda, bağlanmak istediğiniz repo'yu seçin ve ardından **Klon'u**seçin.

      ![Visual Studio'dan oluşturulan "Projeye Bağlan" iletişim kutusu](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda gördükleriniz, erişebildiğiniz Azure DevOps depolarına bağlıdır.

1. Visual Studio repo'nuzu klonladıktan sonra Team Explorer kapanır ve Solution Explorer açılır. Çözümler listesini görüntülemek *için yukarıdaki Çözümler ve Klasörler'e tıklayın*diyen bir ileti görüntülenir. **Çözümleri ve Klasörleri**seçin.

      ![Visual Studio'da Team Explorer'dan "Çözümler ve Klasörler" bildirimi](./media/open-proj-repo-solutions-folders.png)

   Bir çözüm dosyası (özellikle.sln dosyası), "Çözümler ve Klasörler" fly-out menüsünde görünür. Seçin ve Visual Studio çözümünüzü açar.

   Repo'nuzda bir çözüm dosyanız yoksa, çıkış menüsünde "Çözüm Bulunamadı" ifadesi yer almaktadır. Ancak, Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyayı çift tıklatabilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç **penceresinde, Klon'u**seçin veya kodu kullanıma çekin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **Depoya Gözat** bölümünde **Azure DevOps'leri**seçin.

   !['Klon lama veya kodu kullanıma ala' penceresini görüntüleme](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görürseniz, hesabınızda oturum açın.

1. Projeye **Bağlan** iletişim kutusunda, bağlanmak istediğiniz repo'yu seçin ve ardından **Klon'u**seçin.

      ![Visual Studio'dan oluşturulan "Projeye Bağlan" iletişim kutusu](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda gördükleriniz, erişebildiğiniz Azure DevOps depolarına bağlıdır.

   Visual Studio **Team Explorer'ı** açar ve klon tamamlandığında bir bildirim görüntülenir.

     ![Klon tamamlandıktan sonra Visual Studio'daki Team Explorer penceresi](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için **Klasör Görünümü'nu Göster** bağlantısını seçin.

     ![Klon tamamlandıktan sonra Visual Studio'daki Team Explorer penceresinin Çözümler bölümü](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **Çözüm Explorer**açılır.

1. Açılacak bir çözüm dosyası (özellikle .sln dosyası) aramak için **Çözümler ve Klasörler** bağlantısını seçin.

      ![Visual Studio'da Team Explorer'dan "Çözümler ve Klasörler" bildirimi](./media/open-proj-repo-solutions-folders.png)

   Repo'nuzda bir çözüm dosyanız yoksa, "Çözüm Bulunamadı" iletisi görüntülenir. Ancak, Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyayı çift tıklatabilirsiniz.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ile kodlamaya hazırsanız, dile özel aşağıdaki eğitimlerden herhangi biri için dalın:

- [Visual Studio eğitimleri | **C#**](./csharp/index.yml)
- [Visual Studio eğitimleri | **Görsel Temel**](./visual-basic/index.yml)
- [Visual Studio eğitimleri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio eğitimleri | **Piton**](/visualstudio/python/)
- [Visual Studio eğitimleri | **JavaScript**, **TypeScript**, ve **Düğüm.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure DevOps Hizmetleri: Azure Repos ve Visual Studio ile başlayın](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Azure DevOps ile başlayın](/learn/modules/get-started-with-devops/)