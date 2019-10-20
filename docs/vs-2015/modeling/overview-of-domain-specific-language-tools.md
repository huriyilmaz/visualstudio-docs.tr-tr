---
title: Alana Özgü Dil Araçları genel bakış | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652141"
---
# <a name="overview-of-domain-specific-language-tools"></a>Etki Alanına Özgü Dil Araçlarına Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 ' de barındırılan Alana Özgü Dil Araçları (DSL araçları), etki alanına özgü bir dili tasarlamanıza ve ardından kullanıcıların dile göre modeller oluşturmak için sahip olmaları gereken her şeyi oluşturmanıza olanak sağlar.

 Aşağıdaki araçlar DSL araçlarına dahildir:

- Etki alanına özgü dili geliştirmeye başlamanıza yardımcı olması için farklı çözüm şablonları kullanan bir proje Sihirbazı.

- Etki alanına özgü dil tanımınızı oluşturmak ve düzenlemekte bir grafik tasarlayıcı.

- Etki alanına özgü dil tanımının doğru biçimlendirildiğinden emin olan ve sorunlar varsa hataları ve uyarıları görüntüleyen bir doğrulama altyapısı.

- Girdi olarak etki alanına özgü dil tanımı alan ve çıkış olarak kaynak kodu üreten bir kod Oluşturucu.

## <a name="the-dsl-tools-solution"></a>DSL araçları çözümü
 Etki alanına özgü Tasarımcı Sihirbazı aşağıdaki çözüm şablonlarını sağlar:

- Görev akışı

- Sınıf diyagramları

- En az dil

- Bileşen modelleri

- En az WPF

- En az Windows. Forms

- DSL kitaplığı

  Daha fazla bilgi için bkz. [etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Sihirbaz, aşağıdaki projelere sahip bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü oluşturur:

- DSL

   DSL projesi, etki alanına özgü dili ve onun düzen ve işleme araçlarını tanımlar.

- **DslPackage**

   DslPackage projesi dil araçlarının [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ile nasıl tümleşmesini belirler.

## <a name="the-dsl-tools-graphical-interface"></a>DSL araçları grafik arabirimi
 Etki alanına özgü dilinize öğe ve ilişki eklemek için DSL araçları grafik arabirimini kullanabilirsiniz. Öğeleri ekledikten sonra şekilleri şekillere eşleyerek, renkleri özelleştirerek ve dekoratörler ekleyerek görünümlerini tanımlayabilirsiniz. Öğeleri araç kutusuna da ekleyebilirsiniz.

## <a name="validation-in-dsl-tools"></a>DSL araçlarında doğrulama
 DSL, etki alanı modelinin kod oluşturma için temel gereksinimleri karşıladığından emin olmak için bir doğrulama düzeyi sağlar. Genellikle, etki alanına özgü dilinizi oluşturduğunuzda, iş mantığı kurallarınızı ifade etmek için kendi doğrulama bilgilerinizi eklersiniz. Özel doğrulama hakkında daha fazla bilgi için bkz. [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 Tasarlarken, etki alanına özgü dilinizi genellikle doğrulamanızı öneririz. Etki alanına özgü dilinizin doğrulama hataları varsa, kaynak kodu oluşturamazsınız. Şablonlardan kaynak kodu oluşturma işlemi, Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür** ' ü tıklatarak gerçekleştirilir. Dil tanımını her değiştirdiğinizde, **tüm şablonları dönüştürdiğinizden**de emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>DSL araçlarının özelleştirilmesi
 Modelin davranışını iyileştirmek ve dilinizdeki kısıtlamaları tanımlamak için ek kod sağlayabilirsiniz. Gerekirse, metin şablonlarını değiştirerek önemli değişiklikler yapabilirsiniz.

## <a name="distributing-your-dsl-solution"></a>DSL çözümünüzü dağıtma
 DSL araçları, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] barındırılan bir paket oluşturur. Paket, bir araç kutusu, DSL Gezgini ve kullanıcıların, etki alanına özgü dilinizi kullanarak modeller oluşturmalarına izin veren diğer kullanıcı arabirimi öğelerini görüntüler.

 @No__t_0 ' de DSL araçları çözümünü oluşturup çalıştırdığınızda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ikinci bir örneği, etki alanına özgü dilinizin dilin kullanıcısına nasıl göründüğünü gösterir. Her şeyin düzgün çalıştığını doğruladıktan sonra, bulacağınız `.vsix` dosyasını DslPackage projesinin Build klasöründe dağıtabilirsiniz. Bu dosya, DSL 'yi başka bilgisayarlara bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı olarak yüklemek için kullanılabilir.  Daha fazla bilgi için bkz. [etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Deneysel örnek](../extensibility/the-experimental-instance.md) [alana özgü dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
