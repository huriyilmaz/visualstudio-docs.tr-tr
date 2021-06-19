---
title: "Öğretici: Visual Studio 2017'de bir repodan proje açma"
description: Visual Studio 2017'yi kullanarak git veya Azure DevOps deposunda proje açmayı öğrenin.
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
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389208"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Öğretici: Visual Studio 2017'de bir repodan proje açma

Bu öğreticide, Visual Studio 2017'den bir depoya ilk kez bağlanacak ve ondan bir proje açabilirsiniz.

> [!TIP]
> [Visual Studio 2019'da](https://visualstudio.microsoft.com/downloads)Bir GitHub depos ile bağlanmanın yeni, daha tam olarak tümleşik bir yolu var. Daha fazla bilgi için Visual Studio [**2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) sayfasındaki Yeni Git deneyimine bakın.

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Visual Studio 2017'yi kullanarak GitHub Visual Studio açma

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Kaynak Denetiminden **Dosya**  >    >  **Aç Aç'ı seçin.**

   Takım Gezgini **- Bağlan** bölmesi açılır.

    ![Takım Gezgini IDE içindeki Visual Studio penceresi](./media/open-proj-repo-team-explorer.png)

1. Yerel **Git Depoları bölümünde Kopyala'ya** **tıklayın.**

    ![Yerel Git Depoları bölümünden Kopyala'ya tıklayın](./media/open-proj-repo-local-git-repo-clone.png)

1. * öğesinin yer alan kutuya kopyalanan **Git** depolarının URL'sini girin, depo için URL'yi yazın veya yapıştırın ve _*Enter** tuşuna basın. (GitHub'da oturum açmanız isteniyor olabilir; oturum açmanız gerekirse bunu.)

   Bu Visual Studio, Takım Gezgini kopyalar ve Çözüm Gezgini açılır. Çözümler listesini görüntülemek için *yukarıdaki Çözümler ve Klasörler'e tıklayın iletisi görüntülenir.* Çözümler **ve Klasörler'i seçin.**

   ![Dosyadan "Çözümler ve Klasörler" Çözüm Gezgini](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, bu dosya "Çözümler ve Klasörler" açılır menüsünde görünür. Seçin ve Visual Studio açılır.

   ![Açılır listeden neleri açmak Çözüm Gezgini seçin](./media/open-proj-repo-github-solutions-folders-picker.png)

   Bir çözüm dosyanız (özel olarak, bir .sln dosyası) yoksa, açılır menüde "Çözüm Bulunamadı" olur. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirme

Önceki bölümde tamamlamış olduğunuz çalışmaları kontrol etmek için aşağıdaki animasyonu görüntüebilirsiniz.

   ![GitHub deposunu kullanarak proje açma animasyonu Visual Studio](./media/open-project-from-github.gif)

> [!NOTE]
> Visual Studio 2019'a özgü bilgiler için Visual Studio [2019'da bir repodan proje](tutorial-open-project-from-repo-visual-studio-2019.md) açma sayfasına bakın.

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Visual Studio 2017'de kullanarak Azure DevOps bir Visual Studio açma

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Kaynak Denetiminden **Dosya**  >    >  **Aç Aç'ı seçin.**

   Takım Gezgini **- Bağlan** bölmesi açılır.

    ![Takım Gezgini IDE içindeki Visual Studio penceresi](./media/open-proj-repo-team-explorer.png)

1. Veri Azure DevOps bağlanmanın iki yolu vardır:

      - Barındırılan **Hizmet Sağlayıcıları bölümünde Bağlan...** öğesini **seçin.**

        ![Visual Studio IDE içindeki Takım Gezgini penceresinin Barındırılan Hizmet Sağlayıcıları bölümü](./media/open-proj-repo-azure-devops.png)

      - Bağlantıları **Yönet açılan** listesinde Projeye **Bağlan... öğesini seçin.**

        ![Visual Studio IDE içindeki Takım Gezgini penceresinin Bağlantıları Visual Studio bölümü](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Bir **Projeye Bağlan iletişim kutusunda,** bağlanmak istediğiniz bir repo seçin ve ardından Kopyala'ya **tıklayın.**

      ![Dosyadan oluşturulan 'Projeye Bağlan' iletişim Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

1. Bu Visual Studio, Takım Gezgini kopyalar ve Çözüm Gezgini açılır. Çözümler listesini görüntülemek için *yukarıdaki Çözümler ve Klasörler'e tıklayın iletisi görüntülenir.* Çözümler **ve Klasörler'i seçin.**

      ![Visual Studio'de yer alan Takım Gezgini "Çözümler ve Klasörler" Visual Studio](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve Klasörler" açılır menüsünde bir çözüm dosyası (özel olarak bir .sln dosyası) görüntülenir. Seçin ve Visual Studio açılır.

   Bir çözüm dosyanız yoksa, açılır menüde "Çözüm Bulunamadı" ifadesini görünür. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 2017 ile kod vermeye hazırsanız, aşağıdaki dile özgü öğreticilerden herhangi birini gözden alın:

- [Visual Studio öğreticiler | **C#**](./csharp/index.yml)
- [Visual Studio öğreticiler | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticiler | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticiler | **Python**](../python/index.yml)
- [Visual Studio öğreticiler | **JavaScript,** **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2019'da bir repodan proje açma](tutorial-open-project-from-repo-visual-studio-2019.md)
- [Visual Studio 2019'da yeni Git deneyimi](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Kullanmaya başlayın ve Azure Repos ile Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Kullanmaya başlayın ile Azure DevOps](/learn/modules/get-started-with-devops/)
