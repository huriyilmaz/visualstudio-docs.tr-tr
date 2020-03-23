---
title: Etki Alanına Özgü Dil Araçlarına Genel Bakış | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d38aed17d7fdaa694c8c5753705b28b0390dedfc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652141"
---
# <a name="overview-of-domain-specific-language-tools"></a>Etki Alanına Özgü Dil Araçlarına Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Barındırılan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Etki Alanına Özgü Dil Araçları (DSL Araçları), etki alanına özgü bir dil tasarlamanızı ve ardından kullanıcıların dile dayalı modeller oluşturmak için sahip olması gereken her şeyi oluşturmanıza izin verir.

 Aşağıdaki araçlar DSL Tools'a dahildir:

- Etki alanına özgü dilinizi geliştirmeye başlamanıza yardımcı olmak için farklı çözüm şablonları kullanan bir proje sihirbazı.

- Etki alanına özgü dil tanımınızı oluşturmak ve düzenlemek için grafik tasarımcı.

- Etki alanına özgü dil tanımının iyi biçimlendirilmiş olmasını sağlayan ve sorun varsa hataları ve uyarıları görüntüleyen bir doğrulama altyapısı.

- Giriş olarak etki alanına özgü bir dil tanımı alan ve çıktı olarak kaynak kodu üreten bir kod üreteci.

## <a name="the-dsl-tools-solution"></a>DSL Araçları Çözümü
 Etki Alanına Özgü Tasarımcı Sihirbazı aşağıdaki çözüm şablonlarını sağlar:

- Görev Akışı

- Sınıf Diyagramları

- Minimal Dil

- Bileşen Modelleri

- Minimum WPF

- Minimal Windows.Forms

- DSL Kitaplığı

  Daha fazla bilgi için [bkz.](../modeling/choosing-a-domain-specific-language-solution-template.md)

  Sihirbaz, aşağıdaki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeleri içeren bir çözüm oluşturur:

- Dsl

   Dsl projesi etki alanına özgü dili ve düzenleme ve işleme araçlarını tanımlar.

- **Dslpackage**

   DslPackage projesi, dil araçlarının nasıl [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]entegre olduğunu belirler.

## <a name="the-dsl-tools-graphical-interface"></a>DSL Araçları Grafik Arabirimi
 Etki alanına özgü dilinize öğeler ve ilişkiler eklemek için DSL Tools grafik arabirimini kullanabilirsiniz. Öğeleri ekledikten sonra, şekilleri eşleyerek, renkleri özelleştirerek ve dekoratörler ekleyerek görünümlerini tanımlayabilirsiniz. Öğeleri araç kutusuna da ekleyebilirsiniz.

## <a name="validation-in-dsl-tools"></a>DSL Araçlarda Doğrulama
 Dsl, etki alanı modelinin kod oluşturma için temel gereksinimleri karşıladığından emin olmak için bir doğrulama düzeyi sağlar. Genellikle, kendi etki alanına özgü dilinizi oluşturduğunuzda, iş mantığı kurallarınızı ifade etmek için kendi doğrulamanızı eklersiniz. Özel doğrulama hakkında daha fazla bilgi için, [Etki Alanına Özgü Bir Dilde Doğrulama'ya](../modeling/validation-in-a-domain-specific-language.md)bakın.

 Etki alanına özel dilinizi tasarlarken sık sık doğrulamanızı öneririz. Etki alanına özgü dilinizin doğrulama hataları varsa, kaynak kodu oluşturamazsınız. Şablonlardan kaynak kodu oluşturma işlemi, Solution Explorer'ın araç çubuğundaki **Tüm Şablonları Dönüştür'e** tıklayarak gerçekleştirilir. Dil tanımını her değiştirdiğinizde, **Tüm Şablonları**Dönüştürdüğünüzden de emin olun. Daha fazla bilgi için [bkz: Etki Alanına Özel Dil Çözümü Oluşturun.](../modeling/how-to-create-a-domain-specific-language-solution.md)

## <a name="customization-of-dsl-tools"></a>DSL Araçlarının Özelleştirilmesi
 Modelin davranışını hassaslaştırmak ve diliniz üzerindeki kısıtlamaları tanımlamak için ek kod sağlayabilirsiniz. Gerekirse, metin şablonlarını değiştirerek önemli değişiklikler yapabilirsiniz.

## <a name="distributing-your-dsl-solution"></a>DSL Çözümünüzü Dağıtma
 DSL Tools, 'de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]barındırılan bir paket oluşturur. Paket, kullanıcıların etki alanına özgü dilinizi kullanarak modeller oluşturmasına izin veren bir araç kutusu, bir DSL gezgini ve diğer Kullanıcı Arabirimi öğelerini görüntüler.

 DSL Tools çözümünün oluşturulmasını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ve çalıştırDığınızda, ikinci bir örnekte etki alanına özgü dilinizin dilin kullanıcısına nasıl göründüğünü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gösterir. Her şeyin doğru çalıştığını doğruladıktan sonra, `.vsix` DslPackage projesinin yapı klasöründe bulacağınız dosyayı dağıtabilirsiniz. Bu dosya, DSL'yi diğer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bilgisayarlara uzantı olarak yüklemek için kullanılabilir.  Daha fazla bilgi için [bkz.](../modeling/deploying-domain-specific-language-solutions.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Deneysel Örnek](../extensibility/the-experimental-instance.md) [Etki Alanına Özel Dil Araçları Sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
