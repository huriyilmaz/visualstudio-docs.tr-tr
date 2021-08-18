---
title: Etki Alanına Özgü Dil Araçlarına Genel Bakış
description: DSL Araçları'nın etki alanına özgü bir dil tasarlamanızı ve ardından kullanıcıların dile dayalı modeller oluşturmak için sahip olması gereken her şeyi oluşturmanızı nasıl sağlar?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 697c3ee97562cff0a91984cbcfe467a82574a508
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040144"
---
# <a name="overview-of-domain-specific-language-tools"></a>Etki Alanına Özgü Dil Araçlarına Genel Bakış
Domain-Specific'da barındırılan Visual Studio Dil Araçları (DSL Araçları), etki alanına özgü bir dil tasarlamanızı ve ardından kullanıcıların dile dayalı modeller oluşturmak için sahip olması gereken her şeyi oluşturmanızı sağlar.

 DSL Araçları'nın içinde aşağıdaki araçlar yer almaktadır:

- Etki alanına özgü dilinizi geliştirmeye başlamanıza yardımcı olmak için farklı çözüm şablonları kullanan bir proje sihirbazı.

- Etki alanına özgü dil tanımınızı oluşturmaya ve düzenlemeye yönelik bir grafik tasarımcı.

- Etki alanına özgü dil tanımının iyi formed olduğundan emin olan ve sorunlar varsa hataları ve uyarıları görüntüleyen bir doğrulama altyapısı.

- Giriş olarak etki alanına özgü bir dil tanımı alan ve çıkış olarak kaynak kodu üreten bir kod oluşturucu.

## <a name="the-dsl-tools-solution"></a>DSL Araçları Çözümü
 Domain-Specific Tasarımcısı Sihirbazı aşağıdaki çözüm şablonlarını sağlar:

- Görev Flow

- Sınıf Diyagramları

- Minimum Dil

- Bileşen Modelleri

- Minimum WPF

- Minimum Windows. Forms

- DSL Kitaplığı

  Daha fazla bilgi için [bkz. Domain-Specific Dil Çözümü Şablonu Seçme.](../modeling/choosing-a-domain-specific-language-solution-template.md)

  Sihirbaz, aşağıdaki Visual Studio bir çözüm oluşturur:

- Dsl

   Dsl projesi, etki alanına özgü dili ve düzenleme ve işleme araçlarını tanımlar.

- **Dslpackage**

   DslPackage projesi, dil araçlarının Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>DSL Araçları Grafik Arabirimi
 DSL Araçları grafik arabirimini kullanarak etki alanına özgü dilinize öğeler ve ilişkiler ebilirsiniz. Öğeleri ekledikten sonra şekillere eşledikten, renkleri özelleştirerek ve dekoratör ekleyerek bunların görünümünü tanımlayabilirsiniz. Öğeleri araç kutusuna da ekebilirsiniz.

## <a name="validation-in-dsl-tools"></a>DSL Araçlarında Doğrulama
 Dsl, etki alanı modelinin kod oluşturma için temel gereksinimleri karşılamasını sağlayan tek bir doğrulama düzeyi sağlar. Genellikle, etki alanına özgü kendi dilinizi ekleyebilirsiniz, iş mantığı kurallarınızı ifade etmek için kendi doğrulamanızı eklersiniz. Özel doğrulama hakkında daha fazla bilgi için, [bkz. Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

 Tasarlarken etki alanına özgü dilinizi sıklıkla doğrulamanızı öneririz. Etki alanına özgü diliniz doğrulama hataları içeriyorsa kaynak kodu oluşturamazsiniz. Şablonlardan kaynak kodu oluşturma işlemi, kaynak  kodunun araç çubuğundaki Tüm Şablonları Dönüştür'e tık Çözüm Gezgini. Dil tanımını her değiştirerek Tüm Şablonları **Dönüştür'e de sahip olun.** Daha fazla bilgi için, [bkz. How to: Create a Domain-Specific Language Solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>DSL Araçlarını Özelleştirme
 Modelin davranışını geliştirmek ve dilinize göre kısıtlamalar tanımlamak için ek kod sebilirsiniz. Gerekirse, metin şablonlarını değiştirerek önemli değişiklikler yapabilirsiniz.

## <a name="distributing-your-dsl-solution"></a>DSL Çözümlerinizi Dağıtma
 DSL Araçları, içinde barındırılan bir paket Visual Studio. Paket, kullanıcıların etki alanına özgü dilinizi kullanarak model oluşturmasına izin vermenizi sağlarken bir araç kutusu, DSL gezgini ve diğer kullanıcı arabirimi öğelerini görüntüler.

 VISUAL STUDIO'de DSL Araçları çözümünü derlemek ve çalıştırmak için Visual Studio'nin ikinci bir örneği, etki alanına özgü dilinizin dilin kullanıcıya nasıl göründüğünü gösterir. Her şeyin düzgün çalıştığını doğruladikten sonra DslPackage projesinin derleme klasöründe bulursanız dosyayı `.vsix` dağıtabilirsiniz. Bu dosya DSL'i diğer bilgisayarlara bir Visual Studio olarak yüklemek için kullanılabilir.  Daha fazla bilgi için, [bkz. Deploying Domain-Specific Language Solutions](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Deneysel Örnek](../extensibility/the-experimental-instance.md)
- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))