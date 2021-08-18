---
title: ClickOnce Dağıtım Stratejisi | Microsoft Docs
description: ClickOnce uygulaması dağıtma stratejilerini ve dağıtıyor olduğunu uygulamanın türüne bağlı olarak bir strateji seçmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e3b518218204aa6eaeb06bae1cb519f8b4270dc1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073922"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>ClickOnce dağıtım stratejisini seçme
Bir uygulamayı dağıtmak için üç farklı strateji vardır; seçtiğiniz strateji birincil olarak dağıtıyor [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olduğunuz uygulama türüne bağlıdır. Üç dağıtım stratejisi aşağıdaki gibidir:

- Web'den veya bir Ağ Paylaşımı'ndan yükle

- CD'den yükle

- Uygulamayı Web'den veya Ağ Paylaşımı'ndan başlat

    > [!NOTE]
    > Dağıtım stratejisi seçmenin yanı sıra, uygulama güncelleştirmeleri sağlamak için de bir strateji seçmek isteyeceksiniz. Daha fazla bilgi için [bkz. Güncelleştirme ClickOnce seçin.](../deployment/choosing-a-clickonce-update-strategy.md)

## <a name="install-from-the-web-or-a-network-share"></a>Web'den veya bir ağ paylaşımından yükleme
 Bu stratejiyi kullandığınızda, uygulamanız bir Web sunucusuna veya ağ dosyası paylaşımına dağıtılır. Son kullanıcı uygulamayı yüklemek istediğinde, Web sayfası üzerinde bir simgeye tıklar veya dosya paylaşımındaki simgeye çift tıklar. Sonra son kullanıcının bilgisayarında uygulama indirilir, kurulur ve başlatılır. Başlat menüsüne öğeler **eklenir ve** **'de Program Ekle veya** Kaldır **Denetim Masası.**

 Bu strateji ağ bağlantısına bağlı olduğundan, yerel ağ veya yüksek hızlı Internet bağlantısı erişimi olan kullanıcılar çok iyi çalışır.

 Uygulamayı Web'den dağıtırsanız, URL kullanımı etkinleştirildiğinde bağımsız değişkenleri uygulamaya geçirebilirsiniz. Daha fazla bilgi için, [bkz. How to: Retrieve query string information in an online ClickOnce application](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Bu belgede açıklanan diğer yöntemleri kullanarak etkinleştirilen bir uygulamaya bağımsız değişkenler geçirilemez.

 'de bu dağıtım stratejisini etkinleştirmek için Yayımlama Sihirbazı'nın Nasıl Yüklendi sayfasında Web'den veya BIR UNC yolundan veya dosya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paylaşımından'a tıklayın.   

 Bu, varsayılan dağıtım stratejisidir.

## <a name="start-the-application-from-the-web-or-a-network-share"></a>Uygulamayı Web'den veya ağ paylaşımından başlatma
 Uygulamanın bir Web uygulaması gibi davranması dışında, bu strateji birinci stratejiye benzer. Kullanıcı Web sayfası üzerinde bir bağlantıyı tıkladığında (veya dosya paylaşımında bir simgeye çift tıklarsa) uygulama başlatılır. Kullanıcılar uygulamayı kapatınca artık yerel bilgisayarlarında kullanılamaz; içinde Başlat menüsüne veya **Program** Ekle **veya Kaldır seçeneğine** hiçbir **şey Denetim Masası.**

> [!NOTE]
> Teknik olarak uygulama, Web uygulamalarının Web önbelleğine indirilmesi gibi yerel bilgisayar üzerinde uygulama önbelleğine indirilir ve kurulur. Web önbelleği gibi, dosyalar son olarak uygulama önbelleğinden atılır. Ancak, kullanıcı uygulamanın Web'den veya dosya paylaşımından çalıştığını zanneder.

 Bu strateji en iyi seyrek kullanılan uygulamalar için çalışır. Örneğin, genellikle her yıl yalnızca bir kez çalıştırılan bir çalışan-yarar aracı.

 'de bu dağıtım stratejisini etkinleştirmek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için,  Yayımlama **Sihirbazı'nın** Web'den Yükle veya Çalıştır sayfasında Uygulamayı yükleme'ye tıklayın.

 Bu dağıtım stratejisini etkinleştirmek için dağıtım **bildiriminde yükleme** etiketini el ile değiştirebilirsiniz. (Değeri **true** veya **false olabilir.** Bu *Mage.exe,* Uygulama **Türü listesinde Yalnızca** Çevrimiçi **seçeneğini** kullanın.)

## <a name="install-from-a-cd"></a>CD'den yükle
 Bu stratejiyi kullandığınızda, uygulamanız CD-ROM veya DVD gibi çıkarılabilir ortamla dağıtılır. Önceki seçenekte olduğu gibi, kullanıcı uygulamayı yüklemeyi tercih ettiyse yüklenir ve başlar ve  Başlat  menüsüne öğeler eklenir ve uygulamanın içinde Program Ekle veya **Kaldır Denetim Masası.**

 Bu strateji en iyi, devamlı ağ bağlantısı olmayan veya bant genişliği düşük bağlantısı olan kullanıcılara dağıtılacak uygulamalar için çalışır. Uygulama çıkarılabilir ortamdan yüklendiğinden yükleme için ağ bağlantısı gerekmez, ancak ağ bağlantısını yine de uygulama güncelleştirmeleri için gereklidir.

 'de bu dağıtım stratejisini etkinleştirmek için, Yayımlama Sihirbazı'nın Nasıl Yüklenir sayfasında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **cd-ROM veya DVD-ROM'dan'a** tıklayın. 

 Bu dağıtım stratejisini el ile etkinleştirmek için dağıtım **bildiriminde deploymentProvider** etiketini değiştirebilirsiniz. (Visual Studio bu özellik, Project Tasarımcısı'nın **Yayımla** sayfasında Yükleme **URL'si** olarak görünür. Bu *Mage.exe* Başlangıç **Konumu'dır.)**

## <a name="web-browser-support"></a>Web tarayıcısı desteği
 .NET Framework 3.5 kullanan uygulamalar herhangi bir tarayıcı kullanarak yüklenebilir.

 .NET Framework 2.0 kullanan uygulamalar Internet Explorer gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı ile bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Uygulama ClickOnce güvenliğini sağlama](../deployment/securing-clickonce-applications.md)