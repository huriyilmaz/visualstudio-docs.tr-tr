---
title: "öğretici: Visual Studio 2017 ' de bir depoyu bir proje açın"
description: Visual Studio 2017 kullanarak bir Git veya Azure DevOps deposundaki projeyi açmayı öğrenin.
ms.custom: vs-acquisition, get-started
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
ms.openlocfilehash: 5543a568f7246d9600ba375d9a1cf19af4cbd2d4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625971"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>öğretici: Visual Studio 2017 ' de bir depoyu bir proje açın

bu öğreticide, bir depoya ilk kez bağlanmak ve ardından bir projeyi açmak için Visual Studio 2017 kullanacaksınız.

> [!TIP]
> [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)' de GitHub depoya bağlanmak için yeni ve daha tam olarak tümleşik bir yol vardır. daha fazla bilgi için [**Visual Studio 2019 sayfasındaki yeni Git deneyimine**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) bakın.

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Visual Studio 2017 kullanarak GitHub deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda,   >    >  **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini Bağlan** bölmesi açılır.

    ![Visual Studio ıde içindeki Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. **Yerel Git depoları** bölümünde, **Kopyala**' yı seçin.

    ![Yerel Git depoları bölümünden kopyayı seçin](./media/open-proj-repo-local-git-repo-clone.png)

1. ***Kopyalanacak bir git deposunun URL 'Sini girin** _, deponuzu URL 'sini yazın veya yapıştırın ve ardından _ * ENTER * * tuşuna basın. (GitHub oturum açmak için bir istem alabilirsiniz; varsa, bunu yapın.)

   deponuzu Visual Studio klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

   ![Çözüm Gezgini "çözümler ve klasörler" i seçin](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. bunu seçin ve çözümünüzü açar Visual Studio.

   ![Çözüm Gezgini açılır listesinden neleri açmak istediğinizi seçin](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

   ![GitHub deposunda bir proje açma animasyonu Visual Studio kullanılarak başlatılıyor](./media/open-project-from-github.gif)

> [!NOTE]
> Visual Studio 2019 'e özgü bilgiler için [Visual Studio 2019 ' de bir depoyu bir proje açma](tutorial-open-project-from-repo-visual-studio-2019.md) sayfasına bakın.

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Visual Studio 2017 kullanarak Azure DevOps deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda,   >    >  **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini Bağlan** bölmesi açılır.

    ![Visual Studio ıde içindeki Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. işte Azure DevOps depoya bağlanmanın iki yolu vardır:

      - **barındırılan hizmet sağlayıcıları** bölümünde **Bağlan..**. seçeneğini belirleyin.

        ![Visual Studio ıde içindeki Takım Gezgini penceresinin barındırılan hizmet sağlayıcıları bölümü](./media/open-proj-repo-azure-devops.png)

      - **bağlantıları yönet** açılan listesinde **bir Project Bağlan seçin...**

        ![Visual Studio ıde içindeki Takım Gezgini penceresinin bağlantıları yönet bölümü](./media/open-proj-repo-azuredevops-manage-connections.png)

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio tarafından oluşturulan ' Project ' Bağlan bir iletişim kutusu](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > liste kutusunda gördükleriniz, erişiminizin olduğu Azure DevOps depolarına bağlıdır.

1. deponuzu Visual Studio klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

      ![Visual Studio Takım Gezgini "çözümler ve klasörler" bildirimi](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve klasörler" açılan menüsünde bir çözüm dosyası (özellikle bir. sln dosyası) görüntülenir. bunu seçin ve çözümünüzü açar Visual Studio.

   Deponuzda bir çözüm dosyanız yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 2017 ile kod oluşturmaya hazırsanız, dile özgü aşağıdaki öğreticilerden birine gidin:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript**, **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2019 ' de depoyu bir proje açma](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Visual Studio 2019 ' de yeni Git deneyimi](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Azure Repos ve Visual Studio kullanmaya başlayın](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Azure DevOps kullanmaya başlama](/learn/modules/get-started-with-devops/)
