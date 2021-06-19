---
title: 'Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma'
description: Özel bir çözüm kullanarak etki alanına özgü dil (DSL) Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce03349a5179e8dd78220fffd1ff6b21d1a3b495
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387326"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma
Etki alanına özgü bir dil (DSL), özel bir çözüm kullanılarak Visual Studio oluşturulur.

## <a name="prerequisites"></a>Önkoşullar

Bu yordama başlamadan önce şu bileşenleri yükleyin:

- Visual Studio
- Visual Studio SDK (uzantı geliştirme iş **yükünün Visual Studio olarak** yüklenir)
- Modelleme SDK'sı (Visual Studio olarak yüklenir)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Domain-Specific Dili Çözümü Oluşturma

1. DSL Sihirbazı'nı başlatmak için yeni **bir** Alana Özgü Dil Tasarımcısı başlatın.

   > [!NOTE]
   > Tercihen, proje için seçtiğiniz ad geçerli bir Visual C# tanımlayıcısı olmalıdır çünkü kod oluşturmak için kullanılabilir.

   ::: moniker range="vs-2017"

   ![DSL Oluştur iletişim kutusu](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. DSL şablonu seçin.

    Dil **Seçeneklerini Domain-Specific sayfasında,** En Az Dil gibi çözüm şablonlarından **birini seçin.** Oluşturmak istediğiniz DSL'ye benzer bir şablon seçin.

    Çözüm şablonları hakkında daha fazla bilgi için [bkz. Domain-Specific Dil Çözümü Şablonu Seçme.](../modeling/choosing-a-domain-specific-language-solution-template.md)

3. Dosya Uzantısı sayfasına bir dosya **adı uzantısı** girin. Bilgisayarınızda ve DSL'i yüklemek istediğiniz tüm bilgisayarlarda benzersiz olmalıdır. Bu uzantıyı kullanan **uygulama veya Visual Studio yok iletisiyle birlikte bakabilirsiniz.**

   - Tam olarak yüklenmemiş olan önceki deneysel URL'lerde dosya adı uzantısını kullandıysanız,  Visual Studio SDK menüsünde bulunan Deneysel Örneği Sıfırla aracını kullanarak bunları temizlayabilirsiniz.

   - Bu Visual Studio uzantısını kullanan başka bir Uzantı bilgisayarınızda tamamen yüklenmişse, kaldırmayı göz önünde bulundurabilirsiniz. Araçlar menüsünde **Uzantı** **Yöneticisi'ne tıklayın.**

4. Sihirbazın kalan sayfalarındaki alanları inceler ve gerekirse ayarlayın. Ayarlardan memnunsanız Son'a **tıklayın.** Ayarlar hakkında daha fazla bilgi için [bkz. DSL Tasarımcısı Sayfaları.](#settings)

    Sihirbaz, **Dsl** ve **DslPackage** adlı iki projesi olan bir çözüm oluşturur.

   > [!NOTE]
   > Güvenilmeyen kaynaklardan metin şablonları çalıştırmamanızı uyaran bir ileti görüyorsanız Tamam'a **tıklayın.** Bu iletiyi yeniden görünmez olarak ayarlayın.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> DSL Tasarımcısı Sihirbazı Sayfaları
 Bazı alanları varsayılan değerlerinden değiştirmeden bırakın. Ancak, Dosya Uzantısı alanını ayar istediğinizden emin olun.

### <a name="solution-settings-page"></a>Çözüm Ayarları sayfası
 **Etki alanına özgü dilinizi temel alan şablon hangisidir?**
Oluşturmak istediğiniz DSL'ye benzer bir şablon seçin. Farklı şablonlar kolay başlangıç noktaları sağlar. Bir çözüm şablonu seçerek sihirbazda bir açıklama görüntülenir. Çözüm şablonları hakkında daha fazla bilgi için [bkz. Domain-Specific Dil Çözümü Şablonu Seçme.](../modeling/choosing-a-domain-specific-language-solution-template.md)

 **Etki alanına özgü dilinizi nasıl bir adla ifade etmek istiyorsunuz?**
Varsayılan olarak çözüm adı kullanılır. Kod bu değerden oluşturulur. C# sınıf adı olarak geçerli olmalıdır.

### <a name="file-extension-page"></a>Dosya Uzantısı sayfası
 **Model dosyaları hangi uzantıyı kullansın?**
Yeni bir dosya uzantısı yazın.

 Bu dosya uzantısının bu bilgisayarda kullanmak üzere önceden kayıtlı olmadığını aşağıdaki gibi doğrulayın:

 Bu **uzantıyı işlemek için kayıtlı diğer araçlar ve uygulamalar'ın altına bakın.** Bu uzantıyı kullanan **uygulama veya Visual Studio** yok iletisiyle görüyorsanız, bu dosya uzantısını kullanabilirsiniz.

 Araçların veya paketlerin listesini görüyorsanız, aşağıdakilerden birini gerçekleştirin:

- Farklı bir dosya uzantısı yazın.

     \- veya -

- Deneysel Visual Studio sıfırlayın. Bu, daha önce miş olduğunu tüm DSL'lerin kaydını sildi. Başlat menüsünde **Tüm** Programlar'a **tıklayın,** **Microsoft Visual Studio 2010 SDK'sı**, **Araçlar**'ı ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın.** Yeniden kullanmak istediğiniz diğer tüm DSL'leri yeniden oluşturacağız.

     \- veya -

- Bu Visual Studio uzantısını kullanan bir Uzantı bilgisayarınızda tamamen yüklüyse, kaldırın. Araçlar menüsünde **Uzantı** **Yöneticisi'ne tıklayın.**

### <a name="product-settings-page"></a>Ürün Ayarları sayfası
 **Etki alanına özgü yeni dilin ait olduğu ürünün adı nedir?**
Dsl adı varsayılan olarak kullanılır.

 Bu değer Windows Gezgini'nde (veya Dosya Gezgini) bu dosya uzantısına sahip dosyaları açıklamak için kullanılır.

 **Ürünün ait olduğu şirketin adı nedir?**
Şirket adınız.

 Bu değer DSL paketinizin AssemblyInfo özelliklerine dahil edildi.

 **Bu çözümde projeler için kök ad alanı nedir?**
Bu, varsayılan olarak şirket ve ürün adlarından oluşan bir addır.

### <a name="signing-page"></a>İmzalama sayfası
 **Bir güçlü ad anahtar dosyası oluşturma** Varsayılan seçenek, DSL derlemenizi imzalamak için yeni bir anahtar oluşturmaktır.

 **Mevcut güçlü ad anahtarını kullanma** DSL'nizi başka bir derlemeyle tümleştirecekseniz bu seçeneği kullanın.

 Güçlü adlandırma hakkında daha fazla bilgi için [bkz. Derlemeleri Oluşturma Strong-Named Kullanma.](/dotnet/standard/assembly/create-use-strong-named)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))