---
title: SharePoint kodunu doğrulama ve hata ayıklama | Microsoft Docs
description: SharePoint kodunu doğrulayın ve hata ayıklayın. Çözümünüzde geçmiş olayları ve geçerli durumu incelemek için IntelliTrace kullanın. Yöntemlerinizin doğru şekilde çalışmasını sağlamak için birim testi kullanın.
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
ms.workload:
- office
ms.openlocfilehash: d406afbc0a8506262f1bdc17310802b7f41a931a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892144"
---
# <a name="verify-and-debug-sharepoint-code"></a>SharePoint kodunu doğrulama ve hata ayıklama
IntelliTrace ve birim testi kullanarak SharePoint çözümlerinizde daha kolay hata ayıklama yapabilir ve bunların her bir yönteminin doğru şekilde çalıştığından emin olabilirsiniz. Bu özellikleri, diğer proje türleri için aynı yordamları izleyerek Visual Studio 'da SharePoint projeleri için kullanabilirsiniz.

## <a name="intellitrace"></a>IntelliTrace
IntelliTrace kullanarak, SharePoint çözümünüzün yalnızca geçerli durumunu değil, geçmişte ve gerçekleştiği bağlamda gerçekleşen olayları da belirleyebilirsiniz. SharePoint çözümünüzde ilgilendiğiniz olayların kaydedildiği ve her bir noktada değişkenlerin durumlarını ve değerlerini gözden geçibileceğiniz zaman içindeki çeşitli noktalara geri gidebilirsiniz. Bu dinamik gezintiyi kullanarak, çok sayıda kesme noktası ayarlamak zorunda kalmadan SharePoint çözümlerinizde daha hızlı ve kolay bir şekilde hata ayıklama yapabilirsiniz. Ayrıca, hata ayıklama oturumunu bir IntelliTrace günlük (*. iTrace*) dosyasına kaydedebilir, daha sonra Visual Studio Enterprise ' de açabilir ve kilitlenme sonrası hata ayıklaması yapabilirsiniz. *. İTrace* dosyası, belirli SharePoint hatalarının ne zaman ve nasıl gerçekleştiği hakkında ayrıntılı bilgiler içerir, böylece hatalara neden olduğunu daha kolay bir şekilde belirleyebilirsiniz. *. İTrace* dosyasındaki bilgiler, SharePoint 'Teki Birleşik günlük SISTEMININ (ULS) oluşturduğu tüm hata günlüğünün bir alt kümesidir. Bu bilgiler, bir kullanıcı profili açıldığında veya kapandığında ve bir SharePoint projesindeki Özellikler yüklendiğinde, okurken veya değiştirildiğinde, SharePoint 'e özgü olayları içerir. IntelliTrace 'in hangi olaylar için kayıt olduğunu yapılandırabilirsiniz. Daha fazla bilgi için bkz. [kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md).

SharePoint 'te bir hata oluştuğunda hata iletişim kutusu söz konusu hata için bir "bağıntı KIMLIĞI" tanımlayıcısı görüntüler. Ayrıca, *. iTrace* dosyasında listelenen olaylardan bağıntı kimlikleri de alabilirsiniz. Belirli bir bağıntı KIMLIĞIYLE gerçekleşen tüm olayların listesini göstermek için, IntelliTrace Özet sayfasının **analiz** bölümüne kimliği girebilirsiniz. Bu bölümde, yalnızca oluşan olayların adlarını veya olay adlarını, işlev adı, çıkış ve giriş noktaları, parametreler ve dönüş değerleri gibi çağrı bilgileriyle birlikte görüntülemeyi seçebilirsiniz.

**F5** tuşunu seçerek IntelliTrace 'de Visual Studio olaylarını alabilirsiniz. Bununla birlikte, SharePoint 'e özgü olayları almak için, Microsoft Monitoring Agent kullanarak SharePoint Çözümlerinde IntelliTrace verileri toplamanız gerekir. Bu araç IntelliTrace verilerini toplar ve Visual Studio dışında dağıtılan uygulamalar için *. iTrace* dosyaları oluşturur. Daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md) ve [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Birim testi
Birim testi gerçekleştirerek kodunuzda hataları daha kolay bir şekilde bulabilir ve test kodu test yöntemleri içine yazın ve çalıştırın. Bu yöntemler, SharePoint nesne modeline göre projenizin mantığını ve işlevselliğini doğrulamak için kullanabileceğiniz boş değişkenleri ve bir onay ifadesini içerir. Daha fazla bilgi için bkz. [birim testi kodunuz](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes çerçevesi desteği
SharePoint projeleri, .NET Framework dayalı uygulamalarda temsilci tabanlı test saplamaları ve parçalar oluşturabileceğiniz bir yalıtım çerçevesi olan Microsoft Fakes 'i destekler. Fakes çerçevesini kullanarak, birim testlerinizde işlevsiz uygulamalar oluşturabilir, bakımını yapabilir ve ekleyebilirsiniz. Bu saplamalar ve parçalar, birim testlerinizi ortamdan yalıtır. Geçersiz kılınabilir yöntemlerle arabirimleri veya korumalı olmayan sınıfları tüketen kodu test etmek için saplamalar oluşturabilirsiniz. Sabit kodlanmış çağrıları statik veya geçersiz kılınabilir yöntemlerle alternatif bir dolgu uygulamasına yeniden yönlendirmek için de dolgu oluşturabilirsiniz. Ayrıca, tek tek saplama üyelerinin davranışını dinamik olarak özelleştirmek için saplama türleri ve dolgu türleri olan temsilciler da kullanabilirsiniz. Daha fazla bilgi için bkz. [Microsoft Fakes Ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|IntelliTrace kullanılarak Visual Studio çözümlerinin nasıl daha kolay bir şekilde hata ayıklaması yapılacağını açıklar.|
|[İzlenecek yol: IntelliTrace kullanarak bir SharePoint uygulamasında hata ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|IntelliTrace kullanarak bir SharePoint projesinde kodlama hatalarının nasıl bulunacağını gösterir.|
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Birim testlerini kullanarak kodunuzda mantık hatalarının nasıl bulunacağını açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Kalitesini Geliştirme](../test/improve-code-quality.md)