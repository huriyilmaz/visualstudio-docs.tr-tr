---
title: Visual Studio 'da Python eğitim 6. adım, git ile çalışma
titleSuffix: ''
description: Visual Studio 'nun git ile ilgili özelliklerini kapsayan, Visual Studio 'da Python 'un temel bir anlatımın 6. adımı.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72289711"
---
# <a name="step-6-work-with-git"></a>6. Adım: git ile çalışma

**Önceki adım: [paket yükleyip Python ortamınızı yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio, GitHub ve Azure Repos gibi hizmetlerde yerel Git depoları ve uzak depolarla doğrudan tümleştirme sağlar. Tümleştirme, bir depoyu klonlamak, değişiklikleri yürütmek ve dalları yönetmek içerir.

Bu makalede, var olan bir proje için yerel bir git deposu oluşturmaya yönelik temel bir genel bakış ve Visual Studio 'nun git ile ilgili özelliklerinden bazıları alıştırarak.

1. [Önceki adımdaki](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)proje gibi Visual Studio 'da açık bir proje ile çözüme sağ tıklayın ve **kaynak denetimine çözüm Ekle**' yi seçin. Visual Studio, proje kodunuzu içeren bir yerel Git deposu oluşturur.

1. Visual Studio projenin bir git deposunda yönetildiğini algıladığında git ile ilgili denetimler, Visual Studio penceresinin sağ alt köşesinde görüntülenir. Denetimler bekleyen işlemeler, değişiklikler, deponun adı ve dalı gösterir. Ek bilgi görmek için denetimlerin üzerine gelin.

    ![Visual Studio penceresinde git denetiminin üzerine gelindiğinde ek bilgiler görüntülenir](media/working-with-git-01.png)

1. Yeni bir depo oluşturduğunuzda veya git denetimlerinden birini seçtiğinizde, Visual Studio **Takım Gezgini** penceresini açar. (Pencereyi herhangi bir zamanda **görünümü**  >  ile açabilirsiniz. **Takım Gezgini** menü komutu.) Pencerede, **Takım Gezgini** üstbilgisindeki açılan pencereyi kullanma arasında geçiş yaptığınız üç ana bölme bulunur. Yayımlama işlemleri sağlayan **eşitleme** bölmesi, **anında iletme** denetimini seçtiğinizde de görünür (yukarı ok simgesi):

    ![Yerel bir depo oluşturduktan sonra Visual Studio 'da Takım Gezgini](media/working-with-git-02.png)

1. Kaydedilmemiş değişiklikleri gözden geçirmek ve istediğiniz zaman yürütmek için **değişiklikleri** (veya kurşun kalem simgesiyle git denetimini) seçin.

    ![Kaydedilmemiş değişiklikleri gösteren Visual Studio Takım Gezgini](media/working-with-git-03.png)

    Bu dosya için bir fark görünümü açmak için **değişiklikler** listesinde bir dosyaya çift tıklayın:

    ![Dosyadaki değişiklikler için fark görünümü](media/working-with-git-05.png)

1. Dalları incelemek ve birleştirme ve yeniden temellendirme işlemlerini gerçekleştirmek için **dalları** (veya bir dal adına sahip git denetimini) seçin:

    ![Dalları gösteren Visual Studio 'da Takım Gezgini](media/working-with-git-04.png)

1. Depo adı (önceki görüntüde**CosineWave** ) ile git denetimi seçilerek, **Takım Gezgini** , başka bir depoya hızla geçiş yapmak için kullanabileceğiniz bir **bağlantı** arabirimi gösterir.

1. Yerel bir depo kullanılırken, kaydedilen değişiklikler doğrudan depoya gider. Uzak bir depoya bağlıysanız, **Takım Gezgini**' deki aşağı açılan üstbilgiyi seçin, **eşitleme** bölümüne geçmek için **Eşitle** ' yi seçin ve **çekme** ve **getirme** komutlarıyla birlikte çalışın.

## <a name="go-deeper"></a>Daha derin git

Uzak bir git deposundan bir proje oluşturmaya yönelik kısa bir anlatım için bkz. [hızlı başlangıç: Visual Studio 'Da Python kodu deposunu kopyalama](quickstart-03-python-in-visual-studio-project-from-repository.md).

Birleştirme çakışmalarını işleme, çekme istekleri ile kodu gözden geçirme, yeniden temellendirme ve dallar arasındaki değişiklikleri seçme gibi daha kapsamlı bir öğretici için bkz. [Git ile çalışmaya başlama ve Azure Repos](/azure/devops/repos/git/gitquickstart).

## <a name="tutorial-review"></a>Öğretici incelemesi

Tebrikler, Visual Studio 'da Python 'da bu öğreticiyi tamamlama. Bu öğreticide nasıl yapılacağını öğrendiniz:

- Proje oluşturun ve projenin içeriğini görüntüleyin.
- Kod düzenleyicisini kullanın ve bir proje çalıştırın.
- Yeni kod geliştirmek ve bu kodu düzenleyiciye kolayca kopyalamak için **etkileşimli** pencereyi kullanın.
- Visual Studio hata ayıklayıcısında tamamlanmış bir programı çalıştırın.
- Paket yükleyip Python ortamlarını yönetin.
- Git deposundaki kodla çalışın.

Buradan, aşağıdaki makaleler dahil olmak üzere kavramları ve nasıl yapılır kılavuzlarını keşfedebilirsiniz:

- [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profil Oluşturma](profiling-python-code-in-visual-studio.md)
- [Birim testi](unit-testing-python-in-visual-studio.md)
