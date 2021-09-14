---
title: SharePoint kodu doğrulanıyor ve hata ayıklaması | Microsoft Docs
description: SharePoint kodu doğrulayın ve hata ayıklayın. Çözümünüzde geçmiş olayları ve geçerli durumu incelemek için IntelliTrace kullanın. Yöntemlerinizin doğru şekilde çalışmasını sağlamak için birim testi kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e9307884be7ae0ded9d679cd1d3f60a3661b28b3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636817"
---
# <a name="verify-and-debug-sharepoint-code"></a>SharePoint kodu doğrulama ve hata ayıklama
ıntellitrace ve birim testi kullanarak SharePoint çözümlerinizde daha kolay hata ayıklama yapabilir ve bunların her bir yönteminin doğru şekilde çalıştığından emin olabilirsiniz. bu özellikleri, diğer proje türleri için aynı yordamları izleyerek Visual Studio SharePoint projeler için kullanabilirsiniz.

## <a name="intellitrace"></a>IntelliTrace
ıntellitrace kullanarak, SharePoint çözümünüzün yalnızca geçerli durumunu değil, geçmişte ve gerçekleştiği bağlamda gerçekleşen olayları da belirleyebilirsiniz. SharePoint çözümünüzde, ilgilendiğiniz olayların kaydedildiği ve her bir noktada değişkenlerin durumlarını ve değerlerini gözden geçibileceğiniz zaman içindeki çeşitli noktalara geri gidebilirsiniz. bu dinamik gezintiyi kullanarak, çok sayıda kesme noktası ayarlamak zorunda kalmadan SharePoint çözümlerinizde daha hızlı ve kolay bir şekilde hata ayıklama yapabilirsiniz. ayrıca, hata ayıklama oturumunu bir ıntellitrace günlük (*. itrace*) dosyasına kaydedebilir, daha sonra Visual Studio Enterprise ' de açabilir ve kilitlenme sonrası hata ayıklaması yapabilirsiniz. *. itrace* dosyası, hatalara neyin neden olduğunu daha kolay şekilde belirleyebilmeniz için, belirli SharePoint hatalarının ne zaman ve nerede oluştuğunu gösteren ayrıntılı bilgiler içerir. *. itrace* dosyasındaki bilgiler, SharePoint oluşturulan birleşik günlük sisteminin (ULS) tüm hata günlüğü 'nün bir alt kümesidir. bu bilgiler, bir kullanıcı profili açıldığı veya kapatıldığı zaman ve bir SharePoint projesindeki özellikler yüklendiğinde, okurken veya değiştirildiğinde olduğu gibi SharePoint özgü olayları içerir. IntelliTrace 'in hangi olaylar için kayıt olduğunu yapılandırabilirsiniz. Daha fazla bilgi için bkz. [kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md).

SharePoint bir hata oluştuğunda hata iletişim kutusunda söz konusu hata için bir "bağıntı kimliği" tanımlayıcısı görüntülenir. Ayrıca, *. iTrace* dosyasında listelenen olaylardan bağıntı kimlikleri de alabilirsiniz. Belirli bir bağıntı KIMLIĞIYLE gerçekleşen tüm olayların listesini göstermek için, IntelliTrace Özet sayfasının **analiz** bölümüne kimliği girebilirsiniz. Bu bölümde, yalnızca oluşan olayların adlarını veya olay adlarını, işlev adı, çıkış ve giriş noktaları, parametreler ve dönüş değerleri gibi çağrı bilgileriyle birlikte görüntülemeyi seçebilirsiniz.

**F5** tuşunu seçerek ıntellitrace 'de Visual Studio olayları alabilirsiniz. ancak SharePoint özgü olayları almak için, Microsoft Monitoring Agent kullanarak SharePoint çözümlerinde ıntellitrace verileri toplamanız gerekir. Bu araç IntelliTrace verilerini toplar ve Visual Studio dışında dağıtılan uygulamalar için *. iTrace* dosyaları oluşturur. Daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md) ve [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Birim testi
Birim testi gerçekleştirerek kodunuzda hataları daha kolay bir şekilde bulabilir ve test kodu test yöntemleri içine yazın ve çalıştırın. bu yöntemler, SharePoint nesne modeline göre projenizin mantığını ve işlevselliğini doğrulamak için kullanabileceğiniz boş değişkenleri ve bir onay ifadesini içerir. Daha fazla bilgi için bkz. [birim testi kodunuz](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes framework desteği
SharePoint projeler, .NET Framework dayalı uygulamalarda temsilci tabanlı test saplamaları ve parçalar oluşturabileceğiniz bir yalıtım çerçevesi olan Microsoft Fakes destekler. Fakes çerçevesini kullanarak, birim testlerinizde işlevsiz uygulamalar oluşturabilir, bakımını yapabilir ve ekleyebilirsiniz. Bu saplamalar ve parçalar, birim testlerinizi ortamdan yalıtır. Geçersiz kılınabilir yöntemlerle arabirimleri veya korumalı olmayan sınıfları tüketen kodu test etmek için saplamalar oluşturabilirsiniz. Sabit kodlanmış çağrıları statik veya geçersiz kılınabilir yöntemlerle alternatif bir dolgu uygulamasına yeniden yönlendirmek için de dolgu oluşturabilirsiniz. Ayrıca, tek tek saplama üyelerinin davranışını dinamik olarak özelleştirmek için saplama türleri ve dolgu türleri olan temsilciler da kullanabilirsiniz. Daha fazla bilgi için bkz. [Microsoft Fakes test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|ıntellitrace kullanılarak Visual Studio çözümlerinin nasıl daha kolay bir şekilde hata ayıklaması yapılacağını açıklar.|
|[izlenecek yol: ıntellitrace kullanarak SharePoint uygulamasında hata ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|ıntellitrace kullanılarak SharePoint projesindeki kodlama hatalarının nasıl bulunacağını gösterir.|
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Birim testlerini kullanarak kodunuzda mantık hatalarının nasıl bulunacağını açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Kalitesini Geliştirme](../test/improve-code-quality.md)