---
title: 'Nasıl yapılır: etki alanına özgü dil çözümü oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 227838334067d33c8a50c81d3a3c013c6baee356
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533087"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel bir çözüm kullanılarak, etki alanına özgü dil (DSL) oluşturulur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="prerequisites"></a>Önkoşullar
 Bu yordamı başlatabilmeniz için önce şu bileşenleri yüklemeniz gerekir:

|Ürün|İndirme bağlantısı|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio görselleştirme ve modelleme SDK|[Modelleme SDK Indirmesi](https://www.microsoft.com/download/details.aspx?id=48148)|

## <a name="creating-a-domain-specific-language-solution"></a>Etki alanına özgü dil çözümü oluşturma

#### <a name="to-create-a-domain-specific-language-solution"></a>Etki alanına özgü dil çözümü oluşturmak için

1. DSL Sihirbazı 'Nı başlatın.

   1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

   2. **Yeni Proje** iletişim kutusu görünür.

   3. **Proje türleri**altında **diğer proje türleri** düğümünü genişletin ve **genişletilebilirlik**' e tıklayın.

   4. **Alana özgü dil Tasarımcısı**' ye tıklayın.

   5. **Ad** kutusuna çözüm için bir ad yazın. **Tamam**'a tıklayın.

       **Alana özgü dil Tasarımcısı Sihirbazı** görüntülenir.

      > [!NOTE]
      > Tercihen, yazdığınız adın geçerli bir Visual C# tanımlayıcısı olması gerekir, çünkü kod oluşturmak için kullanılabilir.

      ![DSL oluştur iletişim kutusu](../modeling/media/create-dsldialog.png "Create_DSLDialog")

2. DSL şablonu seçin.

    **Etki alanına özgü dil seçeneklerini seç** sayfasında, **en az dil**gibi çözüm şablonlarından birini seçin. Oluşturmak istediğiniz DSL 'ye benzer bir şablon seçin.

    Çözüm şablonları hakkında daha fazla bilgi için bkz. [etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. **Dosya Uzantısı** sayfasında bir dosya adı uzantısı girin. Bu, bilgisayarınızda ve DSL 'yi yüklemek istediğiniz herhangi bir bilgisayarda benzersiz olmalıdır. **Hiçbir uygulama veya Visual Studio Düzenleyicisi bu uzantıyı kullanmamalıdır**iletisini görmeniz gerekir.

   - Tam yüklenmemiş olan önceki deneysel DSLs 'de dosya adı uzantısını kullandıysanız, bu dosyaları, SDK menüsünde bulunan **deneysel örneği Sıfırla** aracını kullanarak temizleyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

   - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bu dosya uzantısını kullanan başka bir uzantı bilgisayarınızda tamamen yüklüyse, uygulamayı kaldırmayı düşünün. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın.

4. Sihirbazın kalan sayfalarındaki alanları inceleyin ve gerekirse ayarlayın. Ayarlarla ilgili memnun olduğunuzda **son**' a tıklayın. Ayarlar hakkında daha fazla bilgi için bkz. [DSL Tasarımcısı Sihirbazı sayfaları](#settings).

    Sihirbaz, **DSL** ve **DslPackage**adlı iki projeye sahip bir çözüm oluşturur.

   > [!NOTE]
   > Güvenilmeyen kaynaklardan metin şablonlarını çalıştıracağınızı belirten bir ileti görürseniz, **Tamam**' a tıklayın. Bu iletiyi tekrar görünmeyecek şekilde ayarlayabilirsiniz.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a>DSL Tasarımcısı Sihirbazı sayfaları
 Birçok alandan birini varsayılan değerlerinden farklı bırakabilirsiniz. Ancak, dosya uzantısı alanını ayarladığınızdan emin olun.

### <a name="solution-settings-page"></a>Çözüm ayarları sayfası
 **Etki alanına özgü dile hangi şablonu temel almak istiyorsunuz?**
Oluşturmak istediğiniz DSL 'ye benzer bir şablon seçin. Farklı şablonlar, uygun başlangıç noktaları sağlar. Bir çözüm şablonu seçtiğinizde, sihirbaz bir açıklama görüntüler. Çözüm şablonları hakkında daha fazla bilgi için bkz. [etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Etki alanına özgü dilinizi ne adlandırmak istiyorsunuz?**
Çözüm adı varsayılan olarak belirlenmiştir. Kod bu değerden oluşturulur. C# sınıf adı olarak geçerli olmalıdır.

### <a name="file-extension-page"></a>Dosya uzantısı sayfası
 **Model dosyalarının kullanması gereken uzantı nedir?**
Yeni bir dosya uzantısı yazın.

 Bu dosya uzantısının bu bilgisayarda kullanılmak üzere zaten kayıtlı olmadığından emin olun:

 **Bu uzantıyı işlemek için kayıtlı diğer araç ve uygulamalar**bölümüne bakın. **Hiçbir uygulama veya Visual Studio Düzenleyicisi tarafından bu uzantıyı kullanan**bir ileti görürseniz, bu dosya uzantısını kullanabilirsiniz.

 Araçların veya paketlerin bir listesini görürseniz, aşağıdakilerden birini yapmalısınız:

- Farklı bir dosya uzantısı yazın.

     \-veya

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Deneysel örneği sıfırlayın. Bu, daha önce oluşturduğunuz tüm DSLs 'lerin kaydını siler. **Başlat** menüsünde, **tüm programlar**, **Microsoft Visual Studio 2010 SDK**ve **araçlar**' a tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın**. Yeniden kullanmak istediğiniz tüm diğer DSLs 'leri yeniden oluşturabilirsiniz.

     \-veya

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bu dosya uzantısını kullanan bir uzantı bilgisayarınızda tamamen yüklüyse, kaldırın. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın.

### <a name="product-settings-page"></a>Ürün ayarları sayfası
 **Yeni etki alanına özgü dilin ait olduğu ürünün adı nedir?**
DSL adını varsayılan olarak alır.

 Bu değer, bu dosya uzantısına sahip dosyaları anlatmak için Windows Gezgini 'nde (veya dosya Gezgini) kullanılır.

 **Ürünün ait olduğu şirketin adı nedir?**
Şirketinizin adı.

 Bu değer DSL paketinizin AssemblyInfo özelliklerine eklenir.

 **Bu çözümdeki projeler için kök ad alanı nedir?**
Bu, varsayılan olarak şirketinizden ve ürün adınızdan oluşan bir addır.

### <a name="signing-page"></a>İmzalama sayfası
 **Tanımlayıcı ad anahtar dosyası oluşturma** Varsayılan seçenek, DSL derlemenizi imzalamak için yeni bir anahtar oluşturmaktır.

 **Mevcut tanımlayıcı ad anahtarını kullan** DSL 'nizi başka bir derlemeyle bütünleştirmek istiyorsanız bu seçeneği kullanın.

 Tanımlayıcı adlandırma hakkında daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Ayrıca Bkz.
 [Etki alanına özgü dil](../modeling/how-to-define-a-domain-specific-language.md) [alana özgü dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100)) tanımlama
