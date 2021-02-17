---
title: "Öğretici: Visual Studio 2017 ' de bir depoyu bir proje açın"
description: Visual Studio 2017 kullanarak bir git veya Azure DevOps deposunda bir projeyi açmayı öğrenin.
ms.custom: get-started
ms.date: 02/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2017
ms.openlocfilehash: 01aca95bde7a20f746d4faece4090eac60b3849e
ms.sourcegitcommit: 51e4426889ae5f49c69b122e37b3f48aa7a3925d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2021
ms.locfileid: "100542983"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Öğretici: Visual Studio 2017 ' de bir depoyu bir proje açın

Bu öğreticide, bir depoya ilk kez bağlanmak ve ardından projeden bir proje açmak için Visual Studio 2017 ' i kullanacaksınız.

> [!TIP]
> [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)' de bir GitHub deposu ile bağlantı kurmak için yeni ve daha tam olarak tümleşik bir yol vardır. Daha fazla bilgi için bkz. [**Visual Studio 'Da yeni git deneyimi 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) sayfası.

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Visual Studio 2017 kullanarak GitHub deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda,   >    >  **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini-Connect** bölmesi açılır.

    ![Visual Studio IDE içinde Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. **Yerel Git depoları** bölümünde, **Kopyala**' yı seçin.

    ![Yerel Git depoları bölümünden kopyayı seçin](./media/open-proj-repo-local-git-repo-clone.png)

1. ***Kopyalanacak bir git deposunun URL 'Sini girin** _, deponuzu URL 'sini yazın veya yapıştırın ve ardından _ * ENTER * * tuşuna basın. (GitHub 'da oturum açmak için bir istem alabilirsiniz; varsa, bunu yapın.)

   Visual Studio deponuzu klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

   ![Çözüm Gezgini "çözümler ve klasörler" i seçin](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. Bunu seçin ve Visual Studio çözümünüzü açar.

   ![Çözüm Gezgini açılır listesinden neleri açmak istediğinizi seçin](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

   ![Visual Studio kullanarak GitHub deposunda proje açma animasyonu](./media/open-project-from-github.gif)

> [!NOTE]
> Visual Studio 2019 'e özgü bilgiler için bkz. [Visual Studio 'da bir depodan proje açma 2019](tutorial-open-project-from-repo-visual-studio-2019.md) sayfası.

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Visual Studio 2017 kullanarak bir Azure DevOps deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda,   >    >  **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini-Connect** bölmesi açılır.

    ![Visual Studio IDE içinde Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. Azure DevOps deponuza bağlanmanın iki yolu aşağıda verilmiştir:

      - **Barındırılan hizmet sağlayıcıları** bölümünde **Bağlan...** seçeneğini belirleyin.

        ![Visual Studio IDE içinde Takım Gezgini penceresinin barındırılan hizmet sağlayıcıları bölümü](./media/open-proj-repo-azure-devops.png)

      - **Bağlantıları Yönet** açılan listesinde, **bir projeye Bağlan...** seçeneğini belirleyin.

        ![Visual Studio IDE içinde Takım Gezgini penceresinin bağlantıları yönetme bölümü](./media/open-proj-repo-azuredevops-manage-connections.png)

1. **Bir projeye Bağlan** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **Kopyala**' yı seçin.

      ![Visual Studio 'dan oluşturulan ' bir projeye Bağlan ' iletişim kutusu](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda gördükleriniz, erişiminiz olan Azure DevOps depolarına bağlıdır.

1. Visual Studio deponuzu klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

      ![Visual Studio 'daki Takım Gezgini "çözümler ve klasörler" bildirimi](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve klasörler" açılan menüsünde bir çözüm dosyası (özellikle bir. sln dosyası) görüntülenir. Bunu seçin ve Visual Studio çözümünüzü açar.

   Deponuzda bir çözüm dosyanız yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. Ancak, klasörü Visual Studio kod düzenleyicisinde açmak için klasör menüsünden herhangi bir dosyaya çift tıklayabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 2017 ile kod oluşturmaya hazırsanız, dile özgü aşağıdaki öğreticilerden birine gidin:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript**, **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2019 ' de bir depoyu bir projeyi açma](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Visual Studio 2019 'de yeni git deneyimi](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Azure Repos ve Visual Studio ile çalışmaya başlama](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Azure DevOps ile çalışmaya başlama](/learn/modules/get-started-with-devops/)
