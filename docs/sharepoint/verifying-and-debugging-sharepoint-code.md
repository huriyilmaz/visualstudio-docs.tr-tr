---
title: Kod Doğrulama ve SharePoint Ayıklama | Microsoft Docs
description: Kodu doğrulayın ve SharePoint ayıklar. IntelliTrace kullanarak çözümünüzde geçmiş olayları ve geçerli durumu inceleme. Yöntemlerinizin doğru şekilde çalışa olduğundan emin olmak için birim testi kullanın.
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
ms.openlocfilehash: e32ef34e26084df149509a3172d748794784fb45adaead0935db8097cc8cd1c6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367388"
---
# <a name="verify-and-debug-sharepoint-code"></a>Kodu doğrulama ve SharePoint ayıklama
IntelliTrace ve birim testi kullanarak, çözümlerinizi daha kolay SharePoint ayıklayabilirsiniz ve bu çözümlerin her bir yönteminin doğru şekilde çalıştığını doğrulayabilirsiniz. Diğer proje türleriyle aynı yordamları SharePoint kullanarak Visual Studio projelerde bu özellikleri kullanabilirsiniz.

## <a name="intellitrace"></a>ıntellitrace
IntelliTrace'i kullanarak yalnızca çözüm çözüm SharePoint aynı zamanda geçmişte meydana gelen olayları ve bunların meydana geldiği bağlamı da tespit edin. İlgi olaylarının kaydediliyor olduğu ve her noktada değişkenlerin durumlarını ve değerlerini gözden geçirebilirsiniz SharePoint çözümde zaman içinde çeşitli noktalara geri dönebilirsiniz. Bu dinamik gezintiyi kullanarak, çok sayıda kesme noktası ayarlamak zorunda kalmadan SharePoint çözümlerinizin hata ayıklamalarını daha hızlı ve kolay bir şekilde yapabilirsiniz. Ayrıca, hata ayıklama oturumunu bir IntelliTrace günlüğü (*.iTrace*) dosyasına kaydedebilir, daha sonra Visual Studio Enterprise içinde açabilir ve kilitlenme sonrası hata ayıklaması gerçekleştirebilirsiniz. *.iTrace* dosyası, belirli bir hatanın ne zaman ve nerede SharePoint ayrıntılı bilgiler içerir; böylece hatalara neyin neden olduğunu daha kolay anlayabilirsiniz. *.iTrace dosyasındaki* bilgiler, içinde Birleşik Günlük Sistemi'nin (ULS) oluşturduğu tam hata günlüğünün SharePoint kümesidir. Bu bilgiler, bir SharePoint profili açıldığında veya kapatılan ve bir SharePoint projesinin özellikleri yüklendiğinde, okundu veya değiştiriken olduğu gibi, belirli bir kullanıcıya özgü olayları içerir. IntelliTrace kayıtlarını hangi olayları yapılandırabilirsiniz. Daha fazla bilgi için [bkz. Kayıtlı IntelliTrace verilerini kullanma.](../debugger/using-saved-intellitrace-data.md)

Veri kümesinde bir hata SharePoint, hata iletişim kutusunda bu hata için bir "bağıntı kimliği" tanımlayıcısı görüntülenir. .iTrace dosyasında listelenen olaylardan bağıntı *kimliklerini de edinebilirsiniz.* Verilen bağıntı kimliğiyle ilgili tüm olayların listesini görüntülemek için IntelliTrace özet sayfasının **Analysis** bölümüne kimliği girebilirsiniz. Bu bölümde, yalnızca meydana gelen olayların adlarını mı yoksa işlev adı, çıkış ve giriş noktaları, parametreler ve dönüş değerleri gibi çağrı bilgileriyle birlikte olayların adlarını görüntülemeyi seçebilirsiniz.

F5 Visual Studio IntelliTrace'de **olaylarını takip** edin. Ancak, SharePoint'a özgü olayları almak için, SharePoint kullanarak intelliTrace verilerini SharePoint çözümlerde toplamanız Microsoft Monitoring Agent. Bu araç IntelliTrace verilerini toplar ve uygulamanın dışında dağıtılan uygulamalar için *.iTrace* Visual Studio. Daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md) ve [IntelliTrace tek başına toplayıcıyı kullanma.](../debugger/using-the-intellitrace-stand-alone-collector.md)

## <a name="unit-test"></a>Birim Testi
Test yöntemlerinin içinde test kodu yazıp çalıştırarak birim testi gerçekleştirerek kodundaki hataları daha kolay bulabilirsiniz. Bu yöntemler boş değişkenler ve projenizin mantığını ve işlevselliğini tek bir nesne modeline göre doğrulamak için kullanabileceğiniz bir Assert SharePoint içerir. Daha fazla bilgi için [bkz. Kodunuzu Birim Testi.](../test/unit-test-your-code.md)

### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes desteği
SharePoint projeleri, Microsoft Fakes tabanlı uygulamalarda temsilci tabanlı test saplamaları ve dolgular oluşturabilirsiniz yalıtım çerçevesi olan .NET Framework. Fakes çerçevesini kullanarak, birim testlerinize sahte uygulamalar oluşturabilir, bakımını ve siniklersiniz. Bu saplamalar ve dolgular birim testlerinizi ortamdan yalıtır. Geçersiz kılınabilir yöntemlerle arabirimleri veya korumalı olmayan sınıfları tüketen kodu test etmek için saplamalar oluşturabilirsiniz. Sabit kodlu çağrıları statik veya geçersiz kılınamaz yöntemlerle korumalı sınıflara alternatif dolgu uygulamasına yönlendirmek için dolgular oluşturabilirsiniz. Tek tek saplama üyelerinin davranışını dinamik olarak özelleştirmek için, saplama türleri ve dolgu türlerine sahip temsilciler de kullanabilirsiniz. Daha fazla bilgi için bkz. Microsoft Fakes ile [Test Altında Kod Yalıtma.](../test/isolating-code-under-test-with-microsoft-fakes.md)

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|IntelliTrace kullanarak Visual Studio kolayca hata ayıklamayı açıklar.|
|[Kılavuz: IntelliTrace kullanarak SharePoint uygulamanın hata ayıklaması](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|IntelliTrace kullanarak bir SharePoint projesinde kodlama hatalarını bulma adımlarını gösterir.|
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Birim testlerini kullanarak kodunda mantık hatalarını bulmayı açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Kalitesini Geliştirme](../test/improve-code-quality.md)