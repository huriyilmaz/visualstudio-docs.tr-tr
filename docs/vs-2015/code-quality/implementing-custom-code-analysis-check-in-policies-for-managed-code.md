---
title: Yönetilen kod için özel kod analizi Iade Ilkelerini uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1cf759e01e5f152f2220124c90f145bfbbe3c01d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651584"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Yönetilen Kod için Özel Kod Çözümleme İade İlkelerini Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kod analizi iade ilkesi, bir takım projesi üyelerinin, sürüm denetimine iade etmeden önce kaynak kodu üzerinde çalışması gereken bir kurallar kümesini belirtir. Microsoft, kod analizi kurallarını işlevsel alanlara bağlayan standart bir *kural kümeleri* kümesi sağlar. *Özel iade ilkesi kural kümeleri* , takım projesine özel bir kod analizi kuralları kümesi belirtir. Bir kural kümesi bir. RuleSet dosyasında depolanır.

 İade ilkeleri takım projesi düzeyinde ayarlanır ve sürüm denetim ağacındaki bir. RuleSet dosyasının konumuyla belirtilir. Takım ilkesi özel kural kümesinin sürüm denetim konumunda bir kısıtlama yoktur.

 Kod Analizi her proje için Özellikler penceresinde bireysel kod projeleri için yapılandırılır. Bir kod projesi için özel bir kural kümesi, yerel bilgisayardaki. RuleSet dosyasının fiziksel konumuyla belirtilir. Kod projesiyle aynı sürücüde bulunan bir. ruleset dosyası belirtildiğinde, Visual Studio proje yapılandırmasındaki dosyanın göreli yolunu kullanır.

 Takım projesi özel kural kümesi oluşturmak için önerilen bir uygulama, iade ilkesi. ruleset dosyasını herhangi bir kod projesinin parçası olmayan özel bir klasörde depooluşturmaktır. Dosyayı ayrılmış bir klasöre depolarsanız, kural dosyasını kimin düzenleyebileceğini kısıtlayan izinleri uygulayabilir ve projeyi içeren dizin yapısını başka bir dizine veya bilgisayara kolayca taşıyabilirsiniz.

## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Takım projesi özel Iade etme kuralı kümesi oluşturma
 Bir takım projesi için özel bir kural kümesi oluşturmak için, ilk olarak **Kaynak Denetim Gezgini**' de iade ilkesi kural kümesi için özel bir klasör oluşturun. Ardından, kural kümesi dosyasını oluşturur ve dosyayı sürüm denetimine eklersiniz. Son olarak, kural kümesini takım projesi için kod analizi iade etme ilkesi olarak belirtirsiniz.

> [!NOTE]
> Bir takım projesinde bir klasör oluşturmak için, önce takım projesi kökünü yerel bilgisayardaki bir konuma eşlemeniz gerekir. Daha fazla bilgi için bkz. [çalışma alanları oluşturma ve bunlarla çalışma (eski)](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2).

#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>İade İlkesi kural kümesi için sürüm denetim klasörünü oluşturmak için

1. İçinde [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , takım projesi düğümünü genişletin ve ardından **kaynak denetimi**' ne tıklayın.

2. **Klasörler** bölmesinde, takım projesine sağ tıklayın ve ardından **Yeni klasör**' e tıklayın.

3. Ana kaynak denetimi bölmesinde, **Yeni klasör**' e sağ tıklayın, **Yeniden Adlandır**' a tıklayın ve kural kümesi klasörü için bir ad yazın.

#### <a name="to-create-the-check-in-policy-rule-set"></a>İade İlkesi kural kümesini oluşturmak için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Dosya**' ya tıklayın.

2. **Kategoriler** listesinde, **genel**' e tıklayın.

3. **Şablonlar** listesinde, **kod analizi kural kümesi**' ne çift tıklayın.

4. Kural kümesine dahil edilecek kuralları belirtin ve ardından kural kümesi dosyasını oluşturduğunuz kural kümesi klasörüne kaydedin.

     Daha fazla bilgi için bkz. [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md)

#### <a name="to-add-the-rule-set-file-to-version-control"></a>Kural kümesi dosyasını sürüm denetimine eklemek için

1. **Kaynak Denetim Gezgini**' de, yeni klasöre sağ tıklayın ve ardından **öğeleri klasöre Ekle**' ye tıklayın.

     Daha fazla bilgi için bkz. [Sürüm denetimini kullanma](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).

2. Oluşturduğunuz kural kümesi dosyasına tıklayın ve ardından **son**' a tıklayın.

     Dosya kaynak denetimine eklenir ve size kullanıma alındı.

3. **Kaynak Denetim Gezgini** Ayrıntılar penceresinde, dosya adına sağ tıklayın ve ardından **bekleyen değişiklikleri iade et**' e tıklayın.

4. **İade** iletişim kutusunda, bir açıklama ekleme ve ardından **iade etme**seçeneğine tıklayabilirsiniz.

    > [!NOTE]
    > Takım projeniz için bir kod analizi iade etme ilkesi yapılandırdıysanız ve **yalnızca geçerli çözümün parçası olan dosyaları içerecek şekilde zorla iadeyi**seçtiyseniz, bir ilke hatası uyarısı tetiklersiniz. Ilke hatası iletişim kutusunda **İlke hatasını geçersiz kıl ve iade et**' i seçin. Gerekli bir açıklama ekleyin ve ardından **Tamam**' a tıklayın.

#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Kural kümesi dosyasını iade etme ilkesi olarak belirtmek için

1. **Takım** menüsünde **Takım Projesi Ayarları**' nın üzerine gelin ve **kaynak denetimi**' ne tıklayın.

2. **Iade ilkesi**' ne ve ardından **Ekle**' ye tıklayın.

3. **Iade ilkesi** listesinde, **Kod Analizi**' ne çift tıklayın ve **yönetilen kod için kod analizini zorla** onay kutusunun seçili olduğundan emin olun.

4. **Bu kural kümesini Çalıştır** listesinde, öğesine tıklayın **\<Select Rule Set from Source Control>** .

5. Sürüm denetimindeki iade ilkesi kural kümesi dosyasının yolunu yazın.

     Yolun aşağıdaki sözdizimine uygun olması gerekir:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > **Kaynak Denetim Gezgini**' de aşağıdaki yordamlardan birini kullanarak yolu kopyalayabilirsiniz:

    - **Klasörler** bölmesinde, kural kümesi dosyasını içeren klasöre tıklayın. **Kaynak** kutusunda görünen klasörün sürüm denetim yolunu kopyalayın ve kural kümesi dosyasının adını el ile yazın.

    - Ayrıntılar penceresinde, kural kümesi dosyasına sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Genel** sekmesinde, **sunucu adındaki**değeri kopyalayın.

## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Kod projelerini Iade Ilkesi kural kümesine eşitleme
 Kod projesinin Özellikler iletişim kutusunda kod proje yapılandırmasının kod analizi kural kümesi olarak bir takım projesi iade ilkesi kuralı kümesi belirlersiniz. Kural kümesi kod projesiyle aynı sürücüde bulunuyorsa, dosya iletişim kutusundan yol seçildiğinde kural kümesini belirtmek için göreli bir yol kullanılır. Göreli yol, proje özellikleri ayarlarının benzer yerel sürüm denetim yapılarını kullanan diğer bilgisayarlara taşınabilir olmasını sağlar.

#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Bir kod projesinin kural kümesi olarak bir takım projesi kural kümesi belirtmek için

1. Gerekirse, iade ilkesi kural kümesi klasörünü ve sürüm denetiminden dosyayı alın.

     Bu adımı, kural kümesi klasörüne sağ tıklayıp ardından **en son sürümü Al**' a tıklayarak **Kaynak Denetim Gezgini** yapabilirsiniz.

2. **Çözüm Gezgini**, kod projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Kod Analizi ' ne tıklayın**.

4. Gerekirse **yapılandırma** ve **Platform** listelerinde uygun seçeneklere tıklayın.

5. Kod projesi belirtilen yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için **derlemede Kod analizini etkinleştir (CODE_ANALYSIS sabiti tanımlar)** onay kutusunu seçin.

6. Diğer şirketlerden gelen bileşenlerdeki kodu yoksaymak için, **oluşturulan koddan sonuçları bastır** onay kutusunu seçin.

7. **Bu kural kümesini Çalıştır** listesinde, öğesine tıklayın **\<Browse...>** .

8. İade İlkesi kural kümesi dosyasının yerel sürümünü belirtin.
