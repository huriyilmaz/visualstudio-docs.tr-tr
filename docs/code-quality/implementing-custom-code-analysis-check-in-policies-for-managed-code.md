---
title: Yönetilen kod için özel kod analizi iade ilkeleri
ms.date: 11/04/2016
description: Özelleştirilmiş bir kod analizi iade ilkesi oluşturmayı öğrenin. Visual Studio yönetilen kodun Azure DevOps bir proje ilkesine uygun olduğundan emin olun.
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
ms.openlocfilehash: d460c6f8e683254d8d7e709d1ab2eedb3dbc144acd12a7f25839b1ae562fca40
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455315"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Yönetilen Kod için Özel Kod Analizi İade İlkelerini Uygulama

bir kod analizi iade ilkesi, bir Azure DevOps projesinin üyelerinin, sürüm denetimine iade etmeden önce kaynak kodda çalışması gereken bir kurallar kümesini belirtir. Microsoft, kod analizi kurallarını işlevsel alanlara bağlayan standart bir *kural kümeleri* kümesi sağlar. *Özel iade ilkesi kural kümeleri* , bir projeye özgü bir kod analizi kuralları kümesi belirtir. Bir kural kümesi bir. RuleSet dosyasında depolanır.

iade ilkeleri Azure DevOps proje düzeyinde ayarlanır ve sürüm denetim ağacındaki bir. ruleset dosyasının konumuyla belirtilir. Takım ilkesi özel kural kümesinin sürüm denetim konumunda bir kısıtlama yoktur.

Kod Analizi her proje için Özellikler penceresinde bireysel kod projeleri için yapılandırılır. Bir kod projesi için özel bir kural kümesi, yerel bilgisayardaki. RuleSet dosyasının fiziksel konumuyla belirtilir. kod projesiyle aynı sürücüde bulunan bir. ruleset dosyası belirtildiğinde Visual Studio, proje yapılandırmasındaki dosyanın göreli yolunu kullanır.

Azure DevOps projesi özel kural kümesi oluşturmak için önerilen bir uygulama, iade ilkesi. ruleset dosyasını herhangi bir kod projesinin parçası olmayan özel bir klasörde depooluşturmaktır. Dosyayı ayrılmış bir klasöre depolarsanız, kural dosyasını kimin düzenleyebileceğini kısıtlayan izinleri uygulayabilir ve projeyi içeren dizin yapısını başka bir dizine veya bilgisayara kolayca taşıyabilirsiniz.

## <a name="create-the-project-custom-check-in-rule-set"></a>Project özel iade etme kuralı kümesi oluşturma

bir Azure DevOps projesi için özel bir kural kümesi oluşturmak için, önce **Kaynak Denetim Gezgini** içindeki iade ilkesi kural kümesi için özel bir klasör oluşturun. Ardından, kural kümesi dosyasını oluşturur ve dosyayı sürüm denetimine eklersiniz. Son olarak, kural kümesini proje için kod analizi iade etme ilkesi olarak belirtirsiniz.

> [!NOTE]
> Azure DevOps projede bir klasör oluşturmak için önce proje kökünü yerel bilgisayardaki bir konuma eşlemeniz gerekir.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>İade İlkesi kural kümesi için sürüm denetim klasörünü oluşturmak için

1. Takım Gezgini, proje düğümünü genişletin ve ardından **kaynak denetimi**' ne tıklayın.

2. **Klasörler** bölmesinde projeye sağ tıklayın ve ardından **Yeni klasör**' e tıklayın.

3. Ana kaynak denetimi bölmesinde, **Yeni klasör**' e sağ tıklayın, **Yeniden Adlandır**' a tıklayın ve kural kümesi klasörü için bir ad yazın.

### <a name="to-create-the-check-in-policy-rule-set"></a>İade İlkesi kural kümesini oluşturmak için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Dosya**' ya tıklayın.

2. **Kategoriler** listesinde, **genel**' e tıklayın.

3. **şablonlar** listesinde **Code Analysis kural kümesi**' ne çift tıklayın.

4. Kural kümesine dahil edilecek [kuralları belirtin](../code-quality/how-to-create-a-custom-rule-set.md) ve ardından kural kümesi dosyasını oluşturduğunuz kural kümesi klasörüne kaydedin.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Kural kümesi dosyasını sürüm denetimine eklemek için

1. **Kaynak Denetim Gezgini**' de, yeni klasöre sağ tıklayın ve ardından **öğeleri klasöre Ekle**' ye tıklayın.

     Daha fazla bilgi için bkz. [Git ve Azure Repos](/azure/devops/repos/git/overview?view=vsts&preserve-view=true).

2. Oluşturduğunuz kural kümesi dosyasına tıklayın ve ardından **son**' a tıklayın.

     Dosya kaynak denetimine eklenir ve size kullanıma alındı.

3. **Kaynak Denetim Gezgini** Ayrıntılar penceresinde, dosya adına sağ tıklayın ve ardından **bekleyen değişiklikleri iade et**' e tıklayın.

4. **İade** iletişim kutusunda, bir açıklama ekleme ve ardından **iade etme** seçeneğine tıklayabilirsiniz.

    > [!NOTE]
    > Azure DevOps projeniz için bir kod analizi iade ilkesi yapılandırdıysanız ve **yalnızca geçerli çözümün parçası olan dosyaları içerecek şekilde zorla iadeyi** seçtiyseniz, bir ilke hatası uyarısı tetiklersiniz. Ilke hatası iletişim kutusunda **İlke hatasını geçersiz kıl ve iade et**' i seçin. Gerekli bir açıklama ekleyin ve ardından **Tamam**' a tıklayın.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Kural kümesi dosyasını iade etme ilkesi olarak belirtmek için

1. **takım** menüsünde **Project Ayarlar**' nin üzerine gelin ve **kaynak denetimi**' ne tıklayın.

2. **Iade ilkesi**' ne ve ardından **Ekle**' ye tıklayın.

3. **iade ilkesi** listesinde **Code Analysis**' ye çift tıklayın ve **yönetilen kod için Code Analysis uygula** onay kutusunun işaretli olduğundan emin olun.

4. **Bu kural kümesini Çalıştır** listesinde, öğesine tıklayın **\<Select Rule Set from Source Control>** .

5. Sürüm denetimindeki iade ilkesi kural kümesi dosyasının yolunu yazın.

     Yolun aşağıdaki sözdizimine uygun olması gerekir:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > **Kaynak Denetim Gezgini**' de aşağıdaki yordamlardan birini kullanarak yolu kopyalayabilirsiniz:

    - **Klasörler** bölmesinde, kural kümesi dosyasını içeren klasöre tıklayın. **Kaynak** kutusunda görünen klasörün sürüm denetim yolunu kopyalayın ve kural kümesi dosyasının adını el ile yazın.

    - Ayrıntılar penceresinde, kural kümesi dosyasına sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Genel** sekmesinde, **sunucu adındaki** değeri kopyalayın.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Kod projelerini Iade Ilkesi kural kümesine eşitler

Kod projesinin Özellikler iletişim kutusunda kod proje yapılandırmasının kod analizi kural kümesi olarak bir proje iade ilke kuralı kümesi belirlersiniz. Kural kümesi kod projesiyle aynı sürücüde bulunuyorsa, dosya iletişim kutusundan yol seçildiğinde kural kümesini belirtmek için göreli bir yol kullanılır. Göreli yol, proje özellikleri ayarlarının benzer yerel sürüm denetim yapılarını kullanan diğer bilgisayarlara taşınabilir olmasını sağlar.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Bir kod projesinin kural kümesi olarak ayarlanan bir proje kuralı belirtmek için

1. Gerekirse, iade ilkesi kural kümesi klasörünü ve sürüm denetiminden dosyayı alın.

   Bu adımı, kural kümesi klasörüne sağ tıklayıp ardından **en son sürümü Al**' a tıklayarak **Kaynak Denetim Gezgini** yapabilirsiniz.

2. **Çözüm Gezgini**, kod projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Code Analysis ' ye tıklayın**.

4. Gerekirse **yapılandırma** ve **Platform** listelerinde uygun seçeneklere tıklayın.

::: moniker range="vs-2017"

5. kod projesi belirtilen yapılandırma kullanılarak oluşturulduğu her seferinde kod analizini çalıştırmak için, **derlemede Code Analysis etkinleştir**' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

5. Kod projesi belirtilen yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için, **ikili çözümleyiciler** bölümünde **derlemede Çalıştır** ' ı seçin.

::: moniker-end

6. **Bu kural kümesini Çalıştır** listesinde, öğesine tıklayın **\<Browse>** .

8. İade İlkesi kural kümesi dosyasının yerel sürümünü seçin.
