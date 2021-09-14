---
title: Etki Alanına Özgü Dil Çözümü Şablonu Seçme
description: Domain-Specific Dil Tasarımcısı Sihirbazı'nda bulunan çözüm şablonlarından birini seçerek etki alanına özgü bir dil çözümü oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 1b3d680df7f04b91c7640d54d994f38b84e41e10
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625760"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Etki Alanına Özgü Dil Çözümü Şablonu Seçme
Etki alanına özgü bir dil çözümü oluşturmak için, Etki Alanına Özgü Dil Tasarımcısı Sihirbazı'nda Domain-Specific şablonlarından birini seçin. Oluşturmak istediğiniz dile en yakın şablonu seçerek, başlangıç çözümünde yapmak zorunda olduğunuz değişiklikleri en aza yız.

 Aşağıdaki çözüm şablonları, Domain-Specific Dil Tasarımcısı Sihirbazı'nda kullanılabilir.

|Şablon|Özellikler|Description|
|-|-|-|
|Sınıf Diyagramları|- Bölme şekilleri<br />- Sınıf devralma<br />- İlişki devralma<br />- Şekil devralma<br />- İlişki özellikleri|Etki alanına özgü diliniz özellikleri olan varlıklar ve ilişkiler içerirse bu çözüm şablonunu kullanın. Bu şablon, UML sınıf diyagramları gibi etki alanına özgü bir dil oluşturur. Ana varlıklar; ilişkilendirme, genelleştirme ve uygulama ilişkileriyle birlikte sınıflar ve arabirimlerdir. Sınıf veya arabirim, öznitelik listesini içeren bir kutu olarak görünür.|
|Bileşen Diyagramları|- Bağlantı noktaları|Etki alanına özgü diliniz bir yazılım sisteminin bileşenleri, yani bölümlerine sahipse bu çözüm şablonunu kullanın. Bu şablon, UML bileşen diyagramları gibi etki alanına özgü bir dil oluşturur. Ana varlıklar, bileşenlerin dışında küçük şekiller olarak görünen bileşenler ve bağlantı noktalarıdır.|
|Görev Flow Diyagramları|- Görüntü ve geometri şekilleri<br />-   *Swimlanes*|Etki alanına özgü diliniz iş akışları, durumları veya dizileri içerirse bu çözüm şablonunu kullanın. Bu şablon, UML etkinlik diyagramları gibi etki alanına özgü bir dil oluşturur. Ana varlık bir etkinliktir ve ana ilişki etkinlikler arasında bir geçiştir. Şablon başlangıç durumu, son durum ve eşitleme çubuğu gibi birkaç başka öğe içerir.|
|Minimum Dil|- Bir sınıf ve şekil<br />- Bir ilişki ve bağlayıcı|Etki alanına özgü diliniz diğer şablonlara benzemese bu çözüm şablonunu kullanın. Bu şablon, Araç Kutusunda Box ve Line olarak temsil edilen iki sınıfı ve bir ilişkisi olan etki **alanına** özgü **bir** dil **oluşturur.** sınıfının ve her ilişkinin bir örnek dize özelliği vardır.|
|Minimal WinForm Tasarımcısı|- Küçük bir model.<br />- Windows görüntüleyen bir Form.|DSL'nin grafik tasarımcı yerine Windows Form'a bağlı olduğu bir uygulama oluşturmak için bu şablonu kullanın.<br /><br /> Dil için kullanıcı arabirimi gibi davranan form Dsl\UI klasöründedir.<br /><br /> Form tasarımcısını açmadan önce projeyi derlemeniz gerekir.<br /><br /> Daha fazla bilgi için, [bkz. Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimal WPF Tasarımcısı|- Küçük bir model<br />- Windows Presentation Foundation görüntüleyen bir kullanıcı arabirimi|Dsl'nin grafik tasarımcı yerine WPF kullanıcı arabirimine bağlı olduğu bir uygulama oluşturmak için bu şablonu kullanın.<br /><br /> Kullanıcı arabiriminin tasarımcısı Dsl\UI klasöründedir.<br /><br /> Kullanıcı arabirimi tasarımcısını açmadan önce projeyi derlemeniz gerekir.<br /><br /> Daha fazla bilgi için, [bkz. Creating a WPF-Based Domain-Specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|DSL Kitaplığı|- En az kitaplık|Diğer DSL tanımlarına aktarılabilir kısmi bir DSL tanımı oluşturmak için bu şablonu kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dil Araçlarına Genel Bakış](../modeling/overview-of-domain-specific-language-tools.md)
