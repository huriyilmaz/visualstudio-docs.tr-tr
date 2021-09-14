---
title: Yönetilen kod için özel kod analizi iade ilkeleri
ms.date: 11/04/2016
description: Özelleştirilmiş kod analizi iade ilkesi oluşturma hakkında bilgi edinebilirsiniz. Yönetilen kodun bir Visual Studio ilkesine uygun olduğundan emin Azure DevOps bakın.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 07c393bd9ff0a16bf2c2692a2b92425138af5554
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631923"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Yönetilen Kod için Özel Kod Analizi İade İlkelerini Uygulama

Kod analizi iade ilkesi, bir Azure DevOps projesinin üyelerinin sürüm denetimine iade olmadan önce kaynak kod üzerinde çalışması gereken bir kural kümesi belirtir. Microsoft, kod analizi kurallarını *işlevsel alanlara grup* haline getiren bir dizi standart kural kümesi sağlar. *Özel iade ilkesi kural kümeleri,* bir projeye özgü bir dizi kod analizi kuralı belirtir. Kural kümesi bir .ruleset dosyasında depolanır.

Iade ilkeleri proje düzeyinde Azure DevOps ve sürüm denetim ağacında bir .ruleset dosyasının konumu tarafından belirtilir. Takım ilkesi özel kural kümesi sürüm denetimi konumu üzerinde herhangi bir kısıtlama yoktur.

Kod analizi, her projenin özellikler penceresindeki tek tek kod projeleri için yapılandırılır. Bir kod projesi için özel kural kümesi, yerel bilgisayarda .ruleset dosyasının fiziksel konumu tarafından belirtilir. Kod projesiyle aynı sürücüde bulunan bir .ruleset dosyası belirtilirse, Visual Studio proje yapılandırmasındaki dosyanın göreli yolunu kullanır.

Azure DevOps projesi özel kural kümesi oluşturmak için önerilen bir uygulama, iade ilkesi .ruleset dosyasını herhangi bir kod projesinin parçası olmayan özel bir klasörde depolamaktır. Dosyayı ayrılmış bir klasörde depolarsanız kural dosyasını kimlerin düzenleyebiliyor olduğunu kısıtlayan izinler uygulayabilir ve projeyi içeren dizin yapısını kolayca başka bir dizine veya bilgisayara taşıyabilirsiniz.

## <a name="create-the-project-custom-check-in-rule-set"></a>Özel Project Kural Kümesi Oluşturma

Azure DevOps projesi için özel bir kural kümesi oluşturmak üzere, önce Kaynak Denetim Gezgini içinde iade ilkesi kural kümesi için özel **bir klasör oluşturun.** Ardından kural kümesi dosyasını oluşturun ve dosyayı sürüm denetimine ekleyin. Son olarak, proje için kod analizi iade ilkesi olarak kural kümesi belirtirsiniz.

> [!NOTE]
> Bir Azure DevOps projesinde klasör oluşturmak için önce proje kökünü yerel bilgisayarda bir konuma eşlemeniz gerekir.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Iade ilkesi kural kümesi için sürüm denetimi klasörü oluşturmak için

1. Bu Takım Gezgini proje düğümünü genişletin ve Kaynak **Denetimi'ne tıklayın.**

2. Klasörler **bölmesinde projeye** sağ tıklayın ve ardından Yeni Klasör'e **tıklayın.**

3. Ana Kaynak Denetimi bölmesinde Yeni Klasör'e sağ **tıklayın,** Yeniden Adlandır'a tıklayın ve kural kümesi klasörü için bir ad yazın.

### <a name="to-create-the-check-in-policy-rule-set"></a>Iade ilkesi kural kümesi oluşturmak için

1. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** Ardından Dosya'ya **tıklayın.**

2. Kategoriler listesinde **Genel'e** **tıklayın.**

3. Şablonlar **listesinde, Kural** Kümesi'ne **Code Analysis tıklayın.**

4. [Kural kümesine](../code-quality/how-to-create-a-custom-rule-set.md) dahil etmek için kuralları belirtin ve ardından kural kümesi dosyasını oluşturduğunuz kural kümesi klasörüne kaydedin.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Kural kümesi dosyasını sürüm denetimine eklemek için

1. Bu **Kaynak Denetim Gezgini** yeni klasöre sağ tıklayın ve ardından Klasöre **Öğe Ekle'ye tıklayın.**

     Daha fazla bilgi için bkz. [Git ve Azure Repos.](/azure/devops/repos/git/overview?view=vsts&preserve-view=true)

2. Oluşturduğunuz kural kümesi dosyasına ve ardından Son'a **tıklayın.**

     Dosya kaynak denetimine eklenir ve kullanıma alınmış olur.

3. Kaynak Denetim Gezgini **ayrıntıları** penceresinde dosya adına sağ tıklayın ve ardından Bekleyen Değişiklikleri Iade **Edin'e tıklayın.**

4. Giriş **iletişim kutusunda,** bir açıklama ekleme ve ardından Giriş Yap'a tıklama **seçeneğiniz vardır.**

    > [!NOTE]
    > Azure DevOps projeniz için bir kod analizi iade ilkesi yapılandırdıysanız ve Iadeyi yalnızca geçerli çözümün parçası olan dosyaları içermesi için zorla 'yi seçtiyseniz, bir ilke hatası uyarısı tetiklersiniz. İlke Hatası iletişim kutusunda İlke hatalarını geçersiz **kıl'ı seçin ve iadeye devam edin.** Gerekli bir açıklama ekleyin ve ardından Tamam'a **tıklayın.**

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Kural kümesi dosyasını iade ilkesi olarak belirtmek için

1. Takım **menüsünde,** öğesinin üzerine **Project Ayarlar** ve ardından Kaynak **Denetimi'ne tıklayın.**

2. Iade **İlkesi'ne ve** ardından Ekle'ye **tıklayın.**

3. **İlkeyi Iade Edin listesinde,** Code Analysis çift tıklayın ve Yönetilen Kod için Code Analysis zorla **onay** kutusunun seçili olduğundan emin olun.

4. Bu kuralı **çalıştır kümesi listesinde'ye** **\<Select Rule Set from Source Control>** tıklayın.

5. Sürüm denetiminde iade ilke kuralı kümesi dosyasının yolunu yazın.

     Yol aşağıdaki söz dizimine uygun olması gerekir:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > aşağıdaki yordamlardan birini kullanarak yolu kopyalayıp aşağıdaki **Kaynak Denetim Gezgini:**

    - Klasörler **bölmesinde,** kural kümesi dosyasını içeren klasöre tıklayın. Kaynak kutusunda görüntülenen klasörün sürüm denetim yolunu **kopyalayın** ve kural kümesi dosyasının adını el ile yazın.

    - Ayrıntılar penceresinde kural kümesi dosyasına sağ tıklayın ve ardından Özellikler'e **tıklayın.** Genel **sekmesinde,** Sunucu Adı'nda **değerini kopyalayın.**

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Kod Projelerini Iade İlke Kural Kümesiyle Eşitleme

Kod projesinin özellikler iletişim kutusunda bir kod projesi yapılandırmasının kod analizi kural kümesi olarak bir proje iade ilkesi kuralı kümesi belirtirsiniz. Kural kümesi kod projesiyle aynı sürücüde bulunuyorsa, yol dosya iletişim kutusundan seçildiğinde kural kümesi belirtmek için göreli bir yol kullanılır. Göreli yol, proje özellikleri ayarlarının benzer yerel sürüm denetimi yapılarını kullanan diğer bilgisayarlara taşınabilir olması için olanak sağlar.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Kod projesinin kural kümesi olarak bir proje kuralı kümesi belirtmek için

1. Gerekirse, iade ilkesi kural kümesi klasörünü ve dosyasını sürüm denetiminden alın.

   Kural kümesi klasörüne sağ **tık Kaynak Denetim Gezgini** ve ardından En Son Sürümü Al 'a tıklayarak bu adımı daha **sonra gerçekleştirebilirsiniz.**

2. Bu **Çözüm Gezgini,** kod projesine sağ tıklayın ve ardından Özellikler'e **tıklayın.**

3. **Öğesini Code Analysis.**

4. Gerekirse Yapılandırma ve Platform listelerinde uygun **seçeneklere** tıklayın. 

::: moniker range="vs-2017"

5. Kod projesi belirtilen yapılandırma kullanılarak her yapılandırmasını kullanarak yapılandırmasını her yapılandırmasını yapılandırmasını her yapılandırmasını **Code Analysis seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

5. Kod projesinin belirtilen yapılandırma kullanılarak her yapılandırmasını yapılandırmasını  kullanarak her yapılandırmasını derlemesinde kod analizi çalıştırmak için İkili çözümleyiciler **bölümünde Derlemede çalıştır'ı** seçin.

::: moniker-end

6. Bu kuralı **çalıştır kümesi listesinde'ye** **\<Browse>** tıklayın.

8. Iade ilkesi kural kümesi dosyasının yerel sürümünü seçin.
