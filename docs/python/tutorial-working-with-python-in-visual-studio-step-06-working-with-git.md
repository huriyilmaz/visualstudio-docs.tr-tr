---
title: Python in Visual Studio öğreticisi 6. adım, Git ile çalışma
titleSuffix: ''
description: Python'ın Git ile ilgili özelliklerini kapsayan Visual Studio 6. adım. Visual Studio kılavuz.
ms.date: 08/16/2021
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 846dd5b260cc7f309b745a3dc8cfeb54ac69fd12
ms.sourcegitcommit: 51a01cc1f1feeac9432c7989db4578e30a573fa1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2021
ms.locfileid: "122274084"
---
# <a name="step-6-work-with-git"></a>6. Adım: Git ile çalışma

**Önceki adım: [Paketleri yükleme ve Python ortamınızı yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

[!INCLUDE[..get-started/includes/git-source-control.md](../get-started/includes/git-source-control.md)]

::: moniker range="vs-2017"

Visual Studio, yerel Git depoları ve uzak depolar ile GitHub ve Azure Repos. Tümleştirme bir depoyu kopyalamayı, değişiklikleri işlemeyi ve dalları yönetmeyi içerir.

Bu makalede, mevcut bir proje için yerel Git deposu oluşturmaya ve git'in Git ile ilgili bazı özelliklerine Visual Studio temel bir genel bakış sağlar.

1. Önceki adımda yer alan Visual Studio gibi bir proje [](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)açıkken çözüme sağ tıklayın ve Kaynak Denetimine Çözüm **Ekle'yi seçin.** Visual Studio kodunuzu içeren yerel bir Git deposu oluşturur.

1. Bu Visual Studio, projenin Git deposuyla ilgili denetimler, git deposu penceresinin sağ alt köşesinde Visual Studio algılar. Denetimler bekleyen işlemeleri, değişiklikleri, depo adını ve dalı gösterir. Ek bilgileri görmek için denetimlerin üzerine gelin.

    ![Uygulama penceresinde git denetimi üzerine gelindiğinde ek Visual Studio görüntülenir](media/working-with-git-01.png)

1. Yeni bir depo oluşturma veya Git denetimlerini seçme Visual Studio yeni **Takım Gezgini** açılır. (Pencereyi Görünüm ile herhangi bir zamanda **açabilirsiniz**  >  **Takım Gezgini** menü komutu.) Pencerede, üst bilgide açılan pencereyi kullanarak geçiş **Takım Gezgini.** Yayımlama **işlemleri** sağlayan Eşitleme bölmesi, Itme denetimi 'ni **(yukarı** ok simgesi) seçerek de görünür:

    ![Takım Gezgini depoyu Visual Studio sonra yeni bir depo oluşturma](media/working-with-git-02.png)

1. Atlanmamış **değişiklikleri** gözden geçirmek ve istediğiniz zaman işlemek için Değişiklikler'i (veya kalem simgesiyle Git denetimi) seçin.

    ![Takım Gezgini iş Visual Studio değişiklikleri gösteren Visual Studio içinde](media/working-with-git-03.png)

    Değişiklikler listesinde bir dosyaya **çift tıklar** ve bu dosya için bir fark görünümü açın:

    ![Bir dosyada yapılan değişiklikler için fark görünümü](media/working-with-git-05.png)

1. Dalları **incelemek** ve birleştirme ve yeniden tabanı işlemleri gerçekleştirmek için Dallar'ı (veya dal adına sahip Git denetimi) seçin:

    ![Takım Gezgini gösteren Visual Studio içinde](media/working-with-git-04.png)

1. Depo adı (önceki görüntüde **CosineWave)** olan Git denetimi seçerek  **Takım Gezgini** bir Bağlan arabirimi gösterir ve bu arabirimle hızlıca başka bir depoya geçebilirsiniz.

1. Yerel depo kullanırken, işlenen değişiklikler doğrudan depoya gider. Uzak depoya bağlıysanız, **Takım Gezgini'de** açılan üst bilgisini seçin,  Eşitleme bölümüne geçmek  için Eşitle'yi seçin ve burada sunulan **Çekme** ve **Getirme** komutlarıyla birlikte çalışabilirsiniz.

## <a name="go-deeper"></a>Daha derine gitme

Uzak bir Git deposundan proje oluşturma hakkında kısa bir kılavuz için bkz. [Hızlı Başlangıç: Visual Studio'da Python kodu deposu](quickstart-03-python-in-visual-studio-project-from-repository.md)kopyalama.

Birleştirme çakışmalarını işleme, çekme istekleriyle kodu gözden geçirme, dallar arasında yenidenbasing ve tek tek seçme değişiklikleri gibi çok daha kapsamlı bir öğretici için bkz. Git ve Kullanmaya başlayın ile [Azure Repos.](/azure/devops/repos/git/gitquickstart)

::: moniker-end

## <a name="tutorial-review"></a>Öğretici gözden geçirmesi

Python'da bu öğreticiyi tamamladıktan sonra Visual Studio. Bu öğreticide şunların nasıl olduğunu öğrendinsiniz:

- Proje oluşturma ve projenin içeriğini görüntüleme.
- Kod düzenleyicisini kullanın ve bir proje çalıştırın.
- Etkileşimli **pencereyi** kullanarak yeni kod geliştirin ve bu kodu düzenleyiciye kolayca kopyalayın.
- Hata ayıklayıcısında tamamlanmış bir Visual Studio çalıştırın.
- Paketleri yükleyin ve Python ortamlarını yönetin.
- Git deposunda kodla çalışma.

Buradan, aşağıdaki makaleler de dahil olmak üzere Kavramlar ve Nasıl uzalar kılavuzlarını keşfedin:

- [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profil Oluşturma](profiling-python-code-in-visual-studio.md)
- [Birim testi](unit-testing-python-in-visual-studio.md)
