---
title: Python Visual Studio öğretici adım 6, Git ile çalışmak
titleSuffix: ''
description: Visual Studio'daki Python'un Visual Studio'daki temel walkthrough'unun 6.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: cd8ebd706d9228d23eb5d5ce3b1429063bae55e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72289711"
---
# <a name="step-6-work-with-git"></a>Adım 6: Git ile çalışın

**Önceki adım: [Paketleri yükleyin ve Python ortamınızı yönetin](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio, GitHub ve Azure Depoları gibi hizmetlerdeki yerel Git depoları ve uzak depolarla doğrudan entegrasyon sağlar. Tümleştirme, bir depoyu klonlamayı, değişiklikler gerçekleştirmeyi ve şubeleri yönetmeyi içerir.

Bu makalede, varolan bir proje için yerel bir Git deposu oluşturma ve Visual Studio'nun Git ile ilgili bazı özelliklerine alışma temel bir genel bakış sağlar.

1. Önceki [adımdaki](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)proje gibi Visual Studio'da açık olan bir projeyle çözüme sağ tıklayın ve **Kaynak Denetimine Çözüm Ekle'yi**seçin. Visual Studio, proje kodunuzu içeren yerel bir Git deposu oluşturur.

1. Visual Studio, projenin Git deposunda yönetildiğini algıladığında Git ile ilgili denetimler Visual Studio penceresinin sağ alt köşesinde görünür. Denetimler bekleyen commits, değişiklikleri, deponun adını ve dalı gösterir. Ek bilgileri görmek için denetimlerin üzerine titretin.

    ![Visual Studio penceresinde git denetimi üzerinde gezinirken ek bilgiler görüntülenir](media/working-with-git-01.png)

1. Yeni bir depo oluşturduğunuzda veya Git denetimlerinden herhangi birini seçtiğinizde, Visual Studio **Team Explorer** penceresini açar. (Ekibi**Gezgini'ni** **Görüntüle** > menüsü komutuyla istediğiniz zaman pencereyi açabilirsiniz.) Pencere, **Takım Gezgini** üstbilgisindeki açılır pencereyi kullanarak geçiş yaptığınız üç ana bölmeye sahiptir. Yayımlama işlemleri sağlayan **Eşitleme** bölmesi, **Push** denetimini (yukarı ok simgesi) seçtiğinizde de görünür:

    ![Yerel bir depo oluşturduktan sonra Visual Studio'da Team Explorer](media/working-with-git-02.png)

1. İşlenmemiş değişiklikleri gözden geçirmek ve istendiğinde işlemek için **Değişiklikler'i** (veya kalem simgesiyle Git denetimini) seçin.

    ![Visual Studio'da Takım Gezgini taahhüt edilmemiş değişiklikleri gösteriyor](media/working-with-git-03.png)

    Bu dosya için diff görünümü açmak için **Değişiklikler** listesindeki bir dosyayı çift tıklatın:

    ![Dosyadaki değişiklikler için Diff görünümü](media/working-with-git-05.png)

1. Dalları incelemek ve birleştirme ve yeniden temel işlemleri gerçekleştirmek için **Dallar'ı** (veya bir şube adı olan Git denetimini) seçin:

    ![Görsel Stüdyo'da Şubeleri Gösteren Takım Gezgini](media/working-with-git-04.png)

1. Depo adı (Önceki görüntüdeki**CosineWave)** ile Git denetimini seçen **Team Explorer,** hızla tamamen başka bir depoya geçebileceğiniz bir **Connect** arabirimi gösterir.

1. Yerel bir depo kullanırken, taahhüt edilen değişiklikler doğrudan depoya gider. Uzak bir depoya bağlıysanız, Takım Gezgini'ndeki açılır başlığı **Team Explorer**seçin, **Eşitleme** bölümüne geçmek için **Eşitle'yi** seçin ve burada sunulan **Çekme** ve **Getir** komutlarıyla çalışın.

## <a name="go-deeper"></a>Daha derine inin

Uzaktan Git deposundan bir proje oluşturmanın kısa bir bölümü [için, Bkz. Quickstart: Visual Studio'da Python kodunun deposunu klonlayın.](quickstart-03-python-in-visual-studio-project-from-repository.md)

Birleştirme çakışmalarını işleme, kodu çekme istekleriyle gözden geçirme, yeniden basing ve dallar arasında kiraz toplama değişiklikleri dahil olmak üzere çok daha kapsamlı bir öğretici için [bkz.](/azure/devops/repos/git/gitquickstart)

## <a name="tutorial-review"></a>Öğretici inceleme

Visual Studio Python bu öğretici tamamladıktan için tebrikler. Bu öğreticide nasıl öğrenebilirsiniz:

- Projeler oluşturun ve projenin içeriğini görüntüleyin.
- Kod düzenleyicisini kullanın ve bir proje çalıştırın.
- Yeni kod geliştirmek ve bu kodu kolayca düzenleyiciye kopyalamak için **Etkileşimli** pencereyi kullanın.
- Visual Studio hata ayıklama da tamamlanmış bir program çalıştırın.
- Paketleri yükleyin ve Python ortamlarını yönetin.
- Git deposunda kodla çalışın.

Buradan, aşağıdaki makaleler de dahil olmak üzere Kavramlar ve Nasıl Yapılacağını rehberleri inceleyin:

- [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profil oluşturma](profiling-python-code-in-visual-studio.md)
- [Birim testi](unit-testing-python-in-visual-studio.md)
