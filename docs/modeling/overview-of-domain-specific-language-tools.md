---
title: Etki Alanına Özgü Dil Araçlarına Genel Bakış
description: DSL araçlarının, etki alanına özgü bir dili tasarlamanıza ve ardından kullanıcıların dile göre modeller oluşturmak için sahip olmaları gereken her şeyi oluşturmanıza nasıl olanak sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dbae3a1b36e6a948766c7dc31d4a8ea8af6d70c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897768"
---
# <a name="overview-of-domain-specific-language-tools"></a>Etki Alanına Özgü Dil Araçlarına Genel Bakış
Visual Studio 'da barındırılan Domain-Specific dil Araçları (DSL araçları), etki alanına özgü bir dil tasarlamanızı ve ardından kullanıcıların dile göre modeller oluşturmak için sahip olmaları gereken her şeyi oluşturmanıza imkan tanır.

 Aşağıdaki araçlar DSL araçlarına dahildir:

- Etki alanına özgü dili geliştirmeye başlamanıza yardımcı olması için farklı çözüm şablonları kullanan bir proje Sihirbazı.

- Etki alanına özgü dil tanımınızı oluşturmak ve düzenlemekte bir grafik tasarlayıcı.

- Etki alanına özgü dil tanımının doğru biçimlendirildiğinden emin olan ve sorunlar varsa hataları ve uyarıları görüntüleyen bir doğrulama altyapısı.

- Girdi olarak etki alanına özgü dil tanımı alan ve çıkış olarak kaynak kodu üreten bir kod Oluşturucu.

## <a name="the-dsl-tools-solution"></a>DSL araçları çözümü
 Domain-Specific Tasarımcı Sihirbazı aşağıdaki çözüm şablonlarını sağlar:

- Görev akışı

- Sınıf diyagramları

- En az dil

- Bileşen modelleri

- En az WPF

- En az Windows. Forms

- DSL kitaplığı

  Daha fazla bilgi için bkz. [Domain-Specific dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Sihirbaz, aşağıdaki projelere sahip bir Visual Studio çözümü oluşturur:

- DSL

   DSL projesi, etki alanına özgü dili ve onun düzen ve işleme araçlarını tanımlar.

- **DslPackage**

   DslPackage projesi dil araçlarının Visual Studio ile nasıl tümleşmesini belirler.

## <a name="the-dsl-tools-graphical-interface"></a>DSL araçları grafik arabirimi
 Etki alanına özgü dilinize öğe ve ilişki eklemek için DSL araçları grafik arabirimini kullanabilirsiniz. Öğeleri ekledikten sonra şekilleri şekillere eşleyerek, renkleri özelleştirerek ve dekoratörler ekleyerek görünümlerini tanımlayabilirsiniz. Öğeleri araç kutusuna da ekleyebilirsiniz.

## <a name="validation-in-dsl-tools"></a>DSL araçlarında doğrulama
 DSL, etki alanı modelinin kod oluşturma için temel gereksinimleri karşıladığından emin olmak için bir doğrulama düzeyi sağlar. Genellikle, etki alanına özgü dilinizi oluşturduğunuzda, iş mantığı kurallarınızı ifade etmek için kendi doğrulama bilgilerinizi eklersiniz. Özel doğrulama hakkında daha fazla bilgi için bkz. [Domain-Specific dilinde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 Tasarlarken, etki alanına özgü dilinizi genellikle doğrulamanızı öneririz. Etki alanına özgü dilinizin doğrulama hataları varsa, kaynak kodu oluşturamazsınız. Şablonlardan kaynak kodu oluşturma işlemi, Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür** ' ü tıklatarak gerçekleştirilir. Dil tanımını her değiştirdiğinizde, **tüm şablonları dönüştürdiğinizden** de emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: Domain-Specific dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>DSL araçlarının özelleştirilmesi
 Modelin davranışını iyileştirmek ve dilinizdeki kısıtlamaları tanımlamak için ek kod sağlayabilirsiniz. Gerekirse, metin şablonlarını değiştirerek önemli değişiklikler yapabilirsiniz.

## <a name="distributing-your-dsl-solution"></a>DSL çözümünüzü dağıtma
 DSL araçları, Visual Studio 'da barındırılan bir paket oluşturur. Paket, bir araç kutusu, DSL Gezgini ve kullanıcıların, etki alanına özgü dilinizi kullanarak modeller oluşturmalarına izin veren diğer kullanıcı arabirimi öğelerini görüntüler.

 Visual Studio 'da DSL araçları çözümünü oluşturup çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği, etki alanına özgü dilin dilin kullanıcısına nasıl göründüğünü gösterir. Her şeyin düzgün çalıştığını doğruladıktan sonra, `.vsix` bulacağınız dosyayı DslPackage projesinin Build klasöründe dağıtabilirsiniz. Bu dosya, DSL 'yi bir Visual Studio uzantısı olarak diğer bilgisayarlara yüklemek için kullanılabilir.  Daha fazla bilgi için bkz. [Domain-Specific dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Deneysel Örnek](../extensibility/the-experimental-instance.md)
- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))