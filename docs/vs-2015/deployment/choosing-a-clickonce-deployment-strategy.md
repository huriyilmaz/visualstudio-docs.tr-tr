---
title: ClickOnce dağıtım stratejisi seçme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cce51860b335e16fe507b20e41a5adba0b3fa278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805602"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>ClickOnce Dağıtım Stratejisini Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama dağıtmaya yönelik üç farklı strateji vardır [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ; seçtiğiniz strateji birincil olarak dağıttığınız uygulamanın türüne bağlıdır. Üç dağıtım stratejisi aşağıdaki gibidir:  
  
- Web'den veya bir Ağ Paylaşımı'ndan yükle  
  
- CD'den yükle  
  
- Uygulamayı Web'den veya Ağ Paylaşımı'ndan başlat  
  
    > [!NOTE]
    > Dağıtım stratejisi seçmenin yanı sıra, uygulama güncelleştirmeleri sağlamak için de bir strateji seçmek isteyeceksiniz. Daha fazla bilgi için bkz. [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Web'den veya bir Ağ Paylaşımı'ndan yükle  
 Bu stratejiyi kullandığınızda, uygulamanız bir Web sunucusuna veya ağ dosyası paylaşımına dağıtılır. Son kullanıcı uygulamayı yüklemek istediğinde, Web sayfası üzerinde bir simgeye tıklar veya dosya paylaşımındaki simgeye çift tıklar. Sonra son kullanıcının bilgisayarında uygulama indirilir, kurulur ve başlatılır. Öğeler **Başlat** menüsüne ve **Denetim Masası**'Ndaki **Program Ekle veya Kaldır** ' a eklenir.  
  
 Bu strateji ağ bağlantısına bağlı olduğundan, yerel ağ veya yüksek hızlı Internet bağlantısı erişimi olan kullanıcılar çok iyi çalışır.  
  
 Uygulamayı Web'den dağıtırsanız, URL kullanımı etkinleştirildiğinde bağımsız değişkenleri uygulamaya geçirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: sorgu dizesi bilgilerini bir çevrimiçi ClickOnce uygulamasında alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Bu belgede açıklanan diğer yöntemleri kullanarak etkinleştirilen bir uygulamaya bağımsız değişkenler geçirilemez.  
  
 İçinde bu dağıtım stratejisini etkinleştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , **Web 'Den** veya Yayımla sihirbazının **yüklü** olan sayfasında bulunan **bir UNC yolundan veya dosya paylaşımından** ' ya tıklayın.  
  
 Bu, varsayılan dağıtım stratejisidir.  
  
## <a name="install-from-a-cd"></a>CD'den yükle  
 Bu stratejiyi kullandığınızda, uygulamanız CD-ROM veya DVD gibi çıkarılabilir ortamla dağıtılır. Önceki seçenekte olduğu gibi, Kullanıcı uygulamayı yüklemeyi seçtiğinde, yüklenir ve başlatılır, öğeler **Başlat** menüsüne ve **Denetim Masası**'Ndaki **Program Ekle/Kaldır** ' a eklenir.  
  
 Bu strateji en iyi, devamlı ağ bağlantısı olmayan veya bant genişliği düşük bağlantısı olan kullanıcılara dağıtılacak uygulamalar için çalışır. Uygulama çıkarılabilir ortamdan yüklendiğinden yükleme için ağ bağlantısı gerekmez, ancak ağ bağlantısını yine de uygulama güncelleştirmeleri için gereklidir.  
  
 İçinde bu dağıtım stratejisini etkinleştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Yayımlama Sihirbazı 'Nın **yüklü** olan sayfasında **bir CD-ROM veya DVD-ROM ' a** tıklayın.  
  
 Bu dağıtım stratejisini el ile etkinleştirmek için dağıtım bildiriminde **deploymentProvider** etiketini değiştirin. (Visual Studio 'da, bu özellik proje tasarımcısının **Yayımla** sayfasında **yükleme URL 'si** olarak gösterilir. Mage.exe **başlangıç konumudur**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Uygulamayı Web'den veya Ağ Paylaşımı'ndan başlat  
 Uygulamanın bir Web uygulaması gibi davranması dışında, bu strateji birinci stratejiye benzer. Kullanıcı Web sayfası üzerinde bir bağlantıyı tıkladığında (veya dosya paylaşımında bir simgeye çift tıklarsa) uygulama başlatılır. Kullanıcılar uygulamayı kapatsa da, yerel bilgisayarlarında artık kullanılamaz; **Başlat** menüsüne veya **Denetim Masası**'Ndaki **Program Ekle veya Kaldır** 'a hiçbir şey eklenmez.  
  
> [!NOTE]
> Teknik olarak uygulama, Web uygulamalarının Web önbelleğine indirilmesi gibi yerel bilgisayar üzerinde uygulama önbelleğine indirilir ve kurulur. Web önbelleği gibi, dosyalar son olarak uygulama önbelleğinden atılır. Ancak, kullanıcı uygulamanın Web'den veya dosya paylaşımından çalıştığını zanneder.  
  
 Bu strateji en iyi seyrek kullanılan uygulamalar için çalışır. Örneğin, genellikle her yıl yalnızca bir kez çalıştırılan bir çalışan-yarar aracı.  
  
 ' De bu dağıtım stratejisini etkinleştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Yayımla sihirbazının **Web 'den yüklemek veya buradan Çalıştır** sayfasında **uygulamayı yüklemeyin** ' e tıklayın.  
  
 Bu dağıtım stratejisini el ile etkinleştirmek için dağıtım bildiriminde **install** etiketini değiştirin. (Değeri **true** veya **false**olabilir. Mage.exe ' de, **uygulama türü** listesinde **yalnızca çevrimiçi** seçeneğini kullanın.)  
  
## <a name="web-browser-support"></a>Web Tarayıcısı Desteği  
 .NET Framework 3.5 kullanan uygulamalar herhangi bir tarayıcı kullanarak yüklenebilir.  
  
 .NET Framework 2.0 kullanan uygulamalar Internet Explorer gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [ClickOnce Uygulamalarının Güvenliğini Sağlama](../deployment/securing-clickonce-applications.md)
