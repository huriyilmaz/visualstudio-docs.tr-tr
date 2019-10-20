---
title: Takım projesi Iade Ilkeleriyle kod kalitesini artırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e4c234d7b13b5c2211c833ee843ea80649c231a4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667651"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Takım Projesi İade İlkeleriyle Kod Kalitesini Arttırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Team Foundation Sürüm Denetimi (TFVC) kullandığınızda, takım projeleriniz için iade ilkeleri oluşturabilirsiniz. daha iyi kod ve daha verimli grup geliştirmeye neden olan uygulamaları zorlamak için. İade ilkeleri, kodun iade edilene izin verilmesi için takım projesi düzeyinde ayarlanan ve Geliştirici bilgisayarlarında uygulanan kurallardır.

 Bu takım projesi iade ilkelerini belirtebilirsiniz:

- **Derlemeler**: bir derleme sırasında oluşturulan derleme sonlarının, yeni bir İadeden önce düzeltilmesi gerekir.

- **Değişiklik kümesi açıklamaları**: kullanıcıların değişiklikleri iade edilirken yorum sağlamasını gerektirir.

- **Kod Analizi**: iade etmeden önce kod analizinin çalıştırılmasını gerektirir.

- **Iş öğeleri**: bir veya daha fazla iş öğesinin iadele ilişkilendirilmesini gerektirir.

> [!IMPORTANT]
> İade ilkelerini kullanmak için [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)] bağlı olmanız gerekir.

## <a name="common-tasks"></a>Ortak Görevler

|Görev|Destekleyici İçerik|
|----------|------------------------|
|**İade Ilkeleri oluşturma ve kullanma:** @No__t_1 takım projesi ayarlarını kullanarak iade ilkeleri oluşturursunuz.|[Kalite kapıları ayarlama ve zorlama](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Kod Analizi iade Ilkeleri oluşturma ve kullanma:** Standart bir kod analizi kuralları kümesinden seçim yapabilir veya özel bir küme oluşturabilirsiniz.|[Kod Çözümleme İade İlkeleri Oluşturma ve Kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>İlgili görevler

|Görev|Destekleyici İçerik|
|----------|------------------------|
|**Geliştirme ortamınızı ayarlama:** Kodu oluşturabilmeniz veya değiştirebilmeniz için önce uygun kaynak kodu kullanarak geliştirme ve test ortamlarınızı ayarlamanız gerekir. Veritabanlarıyla çalışıyorsanız, çevrimdışı temsiline de erişiminizin olması gerekir.|[Geliştirme ortamlarını ayarlama](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|
|**Geliştirme sürecinde Kod analizini kullanın:** Ekip üyeleri, geliştirme bilgisayarlarında Kod analizini çalıştırır. Visual Studio 'da, geliştiriciler bireysel kod projeleri için kod analizi çalıştırmalarını yapılandırıp çalıştırır, çalıştırmalar tarafından bulunan sorunları görüntüleyip analiz eder ve uyarılar için iş öğeleri oluşturur.|[Uygulama Kalitesini Analiz Etme](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Birim testleri oluşturun ve çalıştırın:** Birim testleri, geliştiricilere ve test edicilere, Visual Basic .NET ve C# C++ projeleri içindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir yol sağlar. Bir birim testi bir kez oluşturulup bir hata tanıtılmasından emin olmak için kaynak kodu her değiştirildiğinde çalıştırılabilir.|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|
|**İş öğelerini ve kusurları izleyin:** İş öğelerini, hem işinizi hem de takım projeniz hakkındaki bilgileri izlemek ve yönetmek için kullanabilirsiniz. İş öğesi, [!INCLUDE[esprfound](../includes/esprfound-md.md)] işin atamasını ve ilerlemesini izlemek için kullandığı bir veritabanı kaydıdır. Müşteri gereksinimleri, ürün hataları ve geliştirme görevleri gibi farklı türde iş öğelerini izlemek için farklı türde iş öğeleri kullanabilirsiniz.|[İşi izleme ve yeniden yönlendirilen &#91;iş akışını yönetme&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|

## <a name="external-resources"></a>Dış kaynaklar

### <a name="guidance"></a>Kılavuz
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](http://go.microsoft.com/fwlink/?LinkID=255188)
