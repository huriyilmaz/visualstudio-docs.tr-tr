---
title: 'İzlenecek yol: özel bir kural kümesini yapılandırma ve kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645748"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>İzlenecek Yol: Özel bir Kural Kümesini Yapılandırma ve Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir sınıf kitaplığında özelleştirilmiş bir *kural kümesi* kullanmak üzere yapılandırılmış kod analizi araçlarının nasıl kullanılacağını gösterir. Çözümünüz için belirttiğiniz proje türüyle ilişkili bir kural kümesi seçebilir veya bir bölünemez şekilde sabitlenebilir sorunlar için eski kodu taramak gibi belirli bir gereksinimi karşılamak üzere alternatif kural kümeleri seçebilirsiniz. Her iki durumda da, kural kümeleri proje gereksinimlerinize göre ince ayar yapmak için özelleştirilebilir.

 Bu kılavuzda, şu işlemlerde ilerleyeceğinizi göreceksiniz:

- Bir sınıf kitaplığı oluşturun.

- **Microsoft temel tasarım kılavuzu kuralları** kod analizi kural kümesini seçin.

- Sınıfına kendi kodunuzu ekleyin.

- Kod analizini çalıştırın.

- Kural kümesini özelleştirin.

- Kod analizini çalıştırın ve kural kümesi özelleştirme davranışının nasıl çalıştığını görün.

## <a name="prerequisites"></a>Prerequisites

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] veya [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Kod Analizi ile kural kümeleri kullanma
 İlk olarak basit bir sınıf kitaplığı oluşturun.

#### <a name="create-a-class-library"></a>Sınıf kitaplığı oluşturma

1. **Dosya** menüsünde **Yeni** ' ye ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Proje türleri**altında, **C#görsel**' e tıklayın.

3. **C#Görsel**altında **sınıf kitaplığı**' nı seçin.

4. **Ad** metin kutusuna **RuleSetSample** yazın ve ardından **Tamam**' a tıklayın.

   Ardından, **Microsoft temel tasarım kılavuzu kuralları** kural kümesini seçersiniz ve projenize kaydetmelisiniz.

#### <a name="select-a-code-analysis-rule-set"></a>Kod analizi kural kümesi seçin

1. **Çözümle** menüsünde, **RuleSetSample Için kod analizini Yapılandır**' ı tıklatın.

    Kod analizi için yapılandırma ayarları görüntülenir.

2. **Bu kural kümesini Çalıştır** açılan listesinde, **Microsoft tüm kurallar**' ı seçin.

    Kullanılabilir kural kümeleri hakkında daha fazla bilgi için bkz. [kod analizi kural kümesi başvurusu](../code-quality/code-analysis-rule-set-reference.md).

    Dosya menüsünde, seçili **öğeleri kaydet** ' e tıklayarak proje dosyasını seçtiğiniz kural kümesi ve ayarları hakkında bilgilerle güncelleştirin.

   > [!TIP]
   > Gerçek dünyada bir durumda, kod analizi ile hedeflemek istediğiniz sorunları önceliklendirerek, **Önerilen en düşük kural** kümesi kümesiyle başlamak ve istenen sorunları düzeltmek ve ardından ' ye artımlı olarak daha fazla kural veya kural kümesi eklemek için iyi bir uygulamadır. ek sorunları bulun ve düzeltin.

   Daha sonra, CA1704 "tanımlayıcılarının doğru yazılması gerekir" kod analizi kuralına ilişkin ihlalleri göstermek için kullanılacak sınıf kitaplığına bazı kodlar ekleyeceksiniz. Daha fazla bilgi için bkz. [CA1704: tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Kendi kodunuzu ekleyin

- Çözüm Gezgini, Class1.cs dosyasını açın ve mevcut kodu şu kodla değiştirin:

  ```
  using System;
  using System.Collections.Generic;
  using System.Text;

  namespace RuleSetSample
  {
      public class Class1
      {
          //The variable parameter names "a" and "b" will cause
          //the warning CA 1704 Microsoft.Naming "Consider
          //providing a more meaningful name" to fire
          public int AddIntegers(int a, int b)
          {

              int sum = a + b;

              return (sum);
          }
      }
  }

  ```

  Artık RuleSetSample projesinde kod analizini çalıştırabilir ve Hata Listesi penceresinde oluşturulan herhangi bir hata ve uyarı bulabilirsiniz.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>RuleSetSample projesinde kod analizini çalıştırma

1. **Çözümle** menüsünde, **RuleSetSample üzerinde Kod analizini Çalıştır**' a tıklayın.

2. Hata Listesi penceresinde **Uyarılar** ' a tıklayın ve ardından uyarıları alfasayısal olarak sıralamak için **Açıklama** sütun başlığına tıklayın.

    Gerçek dünyada bir uygulamada, bu noktada düzeltilmesi gereken herhangi bir kural ihlalini çözecektir veya isteğe bağlı olarak, düzeltme olmadığını saptadıysanız bir kuralı kapatabilir veya gizleyebilirsiniz. Daha fazla bilgi için bkz. [SuppressMessage özniteliğini kullanarak uyarıları gizleme](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. CA1704 uyarılara dikkat edin. Bu kuralda Bu ihlaller, "parametreler için daha anlamlı bir ad sağlamayı düşünün" gerektiğini gösterir. Kodunuzda sorunu düzeltebilir veya bir sonraki yordamda açıklandığı gibi kuralı devre dışı bırakabilirsiniz.

   Sonra, CA1704 uyarısını hariç tutmak için kural kümesini özelleştirecek, "tanımlayıcılar doğru yazılmalıdır".

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Projeniz için kural kümesini belirli bir kuralı devre dışı bırakacak şekilde özelleştirme

1. **Çözümle** menüsünde, **RuleSetSample Için kod analizini Yapılandır**' ı tıklatın.

2. **Bu kural kümesini Çalıştır** açılan listesinde, **Microsoft All Rules** kural kümesinin hala vurgulandığını doğrulayın ve **Aç**' a tıklayın. Kural kümesi sayfası görüntülenir.

3. Microsoft. Naming kategorisi düğümünü genişletin ve ardından CA1704 uyarısını seçin.

4. **Eylem** sütununun altında hiçbiri ' ni seçin **.** Bu, CA1704 Hata Listesi penceresinde bir uyarı veya hata olarak görüntülenmesini önler.

    Şimdi, çeşitli araç çubuğu düğmeleri ve filtreleme seçenekleriyle denemeler yapmak için uygun bir zaman kullanabilirsiniz. Örneğin, belirli bir kuralı veya kuralların kategorisini bulmaya yardımcı olması için **Gruplandırma ölçütü** açılan listesini kullanabilirsiniz. Diğer bir örnek, **eylem** sütunu **yok**olarak ayarlanmış tüm kuralları gizlemek veya göstermek için kural kümesi sayfaları araç çubuğundaki **devre dışı kuralları gizle** düğmesini kullanabileceğiniz bir örnektir. Bu, hala devre dışı bırakmak istediğinizi doğrulamak üzere kapattığınız kuralları taramak istiyorsanız yararlı olabilir.

5. Görünüm menüsünde Özellikler penceresi ' ne tıklayın. Özellikler araç penceresinin Ad kutusuna **özel kurallarımı** yazın. Bu, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE 'de yeni kural kümesinin görünen adını değiştirir.

6. Özelleştirilmiş kural kümesini kaydetmek için **Dosya** menüsünde **Microsoft All Rules. RuleSet öğesini kaydet** ' e tıklayın. Projenizin kök klasörüne gidin. **Dosya adı** metin kutusuna **MyCustomRuleSet**yazın. Özel kural kümesi artık projenizle birlikte kullanılacak şekilde seçilebilir.

   Yeni kural kümesi oluşturulduktan sonra, bununla birlikte yeni kural kümesini kullanmak istediğinizi belirtmek için proje ayarlarınızı yapılandırmanız gerekir.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Projenizle birlikte kullanılacak yeni kural kümesini belirtin

1. Çözüm Gezgini, projeye sağ tıklayın ve ardından **Özellikler**' i seçin.

2. **Özellikler** sekmesinde, **Kod Analizi**' ne tıklayın.

    **Bu kural kümesini Çalıştır** açılan listesinde \<Browse ' ye tıklayın **. >** . Kod projenizin kök klasörüne gidin ve **MyCustomRuleSet. RuleSet**' i seçin. Bu, önceki yordamda oluşturduğunuz yeni kural kümesidir.

3. Proje yapılandırmanızı kaydetmek için **Dosya** menüsünde **Kaydet** ' e tıklayın. Özel kural kümesi artık projenizle birlikte kullanılabilir.

   Son olarak, MyCustomRuleSet kural kümesini kullanarak kod analizini yeniden çalıştıracaksınız. Hata Listesi penceresinin CA1704 performans kuralı ihlalini görüntülemediğine dikkat edin.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>RuleSetSample projesinde kod analizini ikinci kez çalıştırın

1. **Çözümle** menüsünde, **RuleSetSample üzerinde Kod analizini Çalıştır**' a tıklayın.

2. Hata Listesi penceresinde, **Uyarılar**' ı tıklattığınızda, artık "tanımlayıcılar doğru yazılmalıdır" KURALı için CA1704 uyarı ihlallerini görmediğine dikkat edin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: yönetilen kod proje](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [kod analizi kural kümesi başvurusu](../code-quality/code-analysis-rule-set-reference.md) için kod analizini yapılandırma
