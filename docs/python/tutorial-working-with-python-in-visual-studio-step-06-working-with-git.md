---
title: Python in Visual Studio öğreticisi 6. adım, Git ile çalışma
titleSuffix: ''
description: Python'ın Git ile ilgili özelliklerini kapsayan Visual Studio Visual Studio 6. adımı.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 581f2fe50c03f4b77ed87723e2c848adc1c9fed960a9e1b6d551cc1085fb03e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121229318"
---
# <a name="step-6-work-with-git"></a>6. Adım: Git ile çalışma

**Önceki adım: [Paketleri yükleme ve Python ortamınızı yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio, yerel Git depoları ve depolama ve depolama gibi hizmetlerle doğrudan GitHub Azure Repos. Tümleştirme bir depoyu kopyalamayı, değişiklikleri işlemeyi ve dalları yönetmeyi içerir.

Bu makalede, mevcut bir proje için yerel Git deposu oluşturmaya ve git'in Git ile ilgili bazı özelliklerine Visual Studio temel bir genel bakış sağlar.

1. Önceki adımda yer alan Visual Studio gibi bir proje [](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)açıkken çözüme sağ tıklayın ve Kaynak Denetimine Çözüm **Ekle'yi seçin.** Visual Studio proje kodunuzu içeren yerel bir Git deposu oluşturur.

1. Bu Visual Studio Projenin Git deposuyla ilgili denetimler, git deposu penceresinin sağ alt köşesinde Visual Studio algılar. Denetimler bekleyen işlemeleri, değişiklikleri, depo adını ve dalı gösterir. Ek bilgileri görmek için denetimlerin üzerine gelin.

    ![Uygulama penceresinde git denetimi üzerine gelindiğinde ek Visual Studio görünür](media/working-with-git-01.png)

1. Yeni bir depo oluşturma veya Git denetimlerini seçme Visual Studio yeni **Takım Gezgini** açılır. (Pencereyi Görünüm ile herhangi bir zamanda **açabilirsiniz**  >  **Takım Gezgini** menü komutu.) Pencerede üç ana bölme vardır ve bu bölme üst bilgisinde açılan Takım Gezgini **geçiş** yapar. Yayımlama **işlemleri** sağlayan Eşitleme bölmesi, Anında İlerle denetimi **(yukarı** ok simgesi) seçerek de görünür:

    ![Takım Gezgini depoyu Visual Studio sonra yeniden çalışma](media/working-with-git-02.png)

1. atlanmamış **değişiklikleri** gözden geçirmek ve istediğiniz zaman işlemek için Değişiklikler'i (veya kalem simgesiyle Git denetimi) seçin.

    ![Takım Gezgini iş Visual Studio değişikliklerin nasıl gösterilebilir](media/working-with-git-03.png)

    Değişiklikler listesinde bir dosyaya **çift tıklar** ve bu dosya için bir fark görünümü açın:

    ![Bir dosyada yapılan değişiklikler için fark görünümü](media/working-with-git-05.png)

1. Dalları **incelemek** ve birleştirme ve yeniden tabanı işlemleri gerçekleştirmek için Dallar'ı (veya dal adıyla Git denetimi) seçin:

    ![Takım Gezgini gösteren Visual Studio içinde](media/working-with-git-04.png)

1. Depo adıyla Git denetimi seçerek (önceki görüntüde **CosineWave),** **Takım Gezgini** bir **Bağlan** arabirimi gösterir ve bu arabirimle hızlıca başka bir depoya geçebilirsiniz.

1. Yerel depo kullanırken, işlenen değişiklikler doğrudan depoya gider. Uzak depoya bağlıysanız, **Takım Gezgini'de** açılan üst bilgisini seçin,  Eşitleme bölümüne geçmek  için Eşitle'yi seçin ve burada sunulan **Çekme** ve **Getirme** komutlarıyla birlikte çalışabilirsiniz.

## <a name="go-deeper"></a>Daha derine gitme

Uzak bir Git deposundan proje oluşturma hakkında kısa bir kılavuz için bkz. [Hızlı Başlangıç: Visual Studio'da Python kodu deposu](quickstart-03-python-in-visual-studio-project-from-repository.md)kopyalama.

Birleştirme çakışmalarını işleme, çekme istekleriyle kodu gözden geçirme, dallar arasında yenidenbasing ve tek tek seçme değişiklikleri gibi çok daha kapsamlı bir öğretici için bkz. Git ve [Kullanmaya başlayın ile Azure Repos.](/azure/devops/repos/git/gitquickstart)

## <a name="tutorial-review"></a>Öğretici gözden geçirmesi

Visual Studio'da Python'da bu öğreticiyi tamamladıktan Visual Studio. Bu öğreticide şunların nasıl olduğunu öğrendinsiniz:

- Proje oluşturma ve projenin içeriğini görüntüleme.
- Kod düzenleyicisini kullanın ve bir proje çalıştırın.
- Etkileşimli **pencereyi** kullanarak yeni kod geliştirin ve bu kodu düzenleyiciye kolayca kopyalayın.
- Hata ayıklayıcısında tamamlanmış Visual Studio çalıştırın.
- Paketleri yükleyin ve Python ortamlarını yönetin.
- Git deposunda kodla çalışma.

Buradan, aşağıdaki makaleler de dahil olmak üzere Kavramlar ve Nasıl uzalar kılavuzlarını keşfedin:

- [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profil Oluşturma](profiling-python-code-in-visual-studio.md)
- [Birim testi](unit-testing-python-in-visual-studio.md)
