---
title: ClickOnce güncelleştirme stratejisi seçme | Microsoft Docs
description: ClickOnce uygulamasının otomatik güncelleştirmeleri nasıl desteklediğini ve hangi güncelleştirme stratejileri kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5618a8996b9858f0799f2a359573d5b7b9da1ce9
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383163"
---
# <a name="choose-a-clickonce-update-strategy"></a>ClickOnce güncelleştirme stratejisini seçme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , otomatik uygulama güncelleştirmeleri sağlayabilir. Uygulama [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] güncelleştirmelerin kullanılabilir olup olmadığını görmek için uygulama düzenli aralıklarla dağıtım bildirimi dosyasını okur. Kullanılabilir olması durumunda uygulamanın yeni sürümü indirilir ve çalıştırılır. Verimlilik için, sadece değişen dosyalar indirilir.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama tasarlarken, uygulamanın kullanılabilir güncelleştirmeleri denetlemek için hangi stratejiyi kullanacağını belirlemelisiniz. Kullanabileceğiniz üç temel strateji vardır: Uygulama başlangıcında güncelleştirmeleri denetleme, uygulama başlangıcından sonra güncelleştirmeleri denetleme (Arka planda bir iş parçacığı çalıştırılır.) veya güncelleştirmeler için bir kullanıcı arayüzü sağlama.

 Ayrıca, uygulama güncelleştirmelerinin ne sıklıkta denetleneceğini belirleyebilirsiniz ve gerekli güncelleştirmeleri yapabilirsiniz.

> [!NOTE]
> Uygulama güncelleştirmeleri, ağ bağlantısı gerektirir. Ağ bağlantısı mevcut değilse, uygulama güncelleştirme stratejisi ne olursa olsun güncelleştirmeleri denetlemeden çalışacaktır.

> [!NOTE]
> .NET Framework 2,0 ve .NET Framework 3,0 ' de, uygulamanız güncelleştirmeleri her denetlediğinde, başlangıçtan önce veya sonra veya \<xref:System.Deployment.Application> API 'leri kullanarak, `deploymentProvider` dağıtım bildiriminde ayarlamanız gerekir. `deploymentProvider`Öğesi, **Yayımla** sekmesinin **güncelleştirmeler** Iletişim kutusundaki **konum Güncelleştir** alanına Visual Studio 'ya karşılık gelir. Bu kural .NET Framework 3,5 ' de rahat. Daha fazla bilgi için bkz. [sınama ve üretim sunucuları için teslim etmeden ClickOnce uygulamaları dağıtma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

## <a name="check-for-updates-after-application-startup"></a>Uygulama başlangıcından sonra güncelleştirmeleri denetle
 Bu stratejiyi kullanarak, uygulama çalışırken, arka planda dağıtım dosyası bildiriminin yerini belirleyip okumayı deneyecektir. Bir güncelleştirme erişilebilirse, kullanıcının uygulamayı sonraki çalıştırmasında, kullanıcı güncelleştirmeyi indirmek ve kurmak için uyarılacaktır.

 Bu strateji en iyi uzun indirmelere ihtiyaç duyacak büyük uygulamalar için veya düşük bant genişliğine sahip ağ bağlantıları için çalışır.

 Bu güncelleştirme stratejisini etkinleştirmek için, uygulama **güncelleştirmeleri** iletişim kutusunda uygulamanın **güncelleştirmeleri denetlemesi gereken seçeneği belirleyin** bölümünde **uygulama başladıktan sonra** ' ye tıklayın. Sonra, **uygulamanın güncelleştirmeleri ne sıklıkta denetlemesi gerektiğini belirtmek** için bölümünde bir güncelleştirme aralığı belirtin.

 Bu, dağıtım bildiriminde **Update** öğesini şu şekilde değiştirme ile aynıdır:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <expiration maximumAge="6" unit="hours" />
   </update>
</subscription>
```

## <a name="check-for-updates-before-application-startup"></a>Uygulama başlangıcından önce güncelleştirmeleri denetle
 Varsayılan strateji, uygulama başlatılmadan önce dağıtım bildirimi dosyasının yerini belirleyip okumayı denemektir. Bu strateji kullanarak, kullanıcı uygulamayı her başlattığında, uygulama dağıtım bildirim dosyasının yerini belirleyip okumaya çalışacaktır. Bir güncelleştirme kullanılabilirse, indirilip başlatılacaktır; aksi durumda uygulamanın var olan sürümü başlatılır.

 Bu strateji en iyi yüksek bant genişliğine sahip ağ bağlantıları için çalışır; uygulama başlatımındaki gecikme düşük bantlı bağlantılar için kabul edilemeyecek kadar uzun olabilir.

 Bu güncelleştirme stratejisini etkinleştirmek için, uygulama **güncelleştirmeleri** iletişim kutusunda uygulamanın **güncelleştirmeleri denetlemelidir seçeneğini belirleyin** bölümünde **uygulama başlamadan önce** ' ye tıklayın.

 Bu, dağıtım bildiriminde **Update** öğesini şu şekilde değiştirme ile aynıdır:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <beforeApplicationStartup />
   </update>
</subscription>
```

## <a name="make-updates-required"></a>Gerekli güncelleştirmeleri yapın
 Kullanıcıların uygulamanızın güncelleştirilmiş bir sürümünü çalıştırmasını istediğiniz durumlar olabilir. Örneğin, çalışan uygulamanızın daha eski bir sürümünün doğru olarak çalışmasını engelleyen bir Web hizmeti gibi harici bir kaynakta değişiklik yapabilirsiniz. Bu durumda, güncelleştirmenizi gerekli olarak işaretlemek ve kullanıcıların daha eski sürümleri çalıştırmasını engellemek isteyeceksinizdir.

> [!NOTE]
> Diğer güncelleştirme stratejilerini kullanarak güncelleştirmeler gerektirseniz de, **uygulama başlamadan önce** denetim, eski bir sürümün çalıştırılabilmesi için tek yoldur. Zorunlu güncelleştirme başlangıçta algılandığında, kullanıcının ya güncelleştirmeyi kabul etmesi ya da uygulamayı kapatması gerekir.

 Bir güncelleştirmeyi gerekli olarak işaretlemek için, **uygulama güncelleştirmeleri** iletişim kutusunda **Bu uygulama için gereken en düşük sürümü belirtin** ' e tıklayın ve ardından yüklenebilen uygulamanın en düşük sürüm numarasını belirten yayımlama sürümünü ( **ana** , **İkincil** , **derleme** , **Düzeltme** ) belirtin.

 Bu, dağıtım bildiriminde **dağıtım** öğesinin **MinimumRequiredVersion** özniteliğini ayarlamayla aynıdır; Örneğin:

```xml
<deployment install="true" minimumRequiredVersion="1.0.0.0">
```

## <a name="specify-update-intervals"></a>Güncelleştirme aralıklarını belirtin
 Uygulamanın güncelleştirmeleri ne sıklıkta denetleyeceğini de belirtebilirsiniz. Bunu yapmak için, bu konuda "Uygulama Başlangıcından Sonra Güncelleştirmeleri Denetleme" bölümünde bahsedildiği gibi uygulamanın güncelleştirmeleri başlangıçtan sonra denetleyeceğini belirtin.

 Güncelleştirme aralığını belirtmek için uygulama **güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirme özelliklerini ne sıklıkla denetlemesi gerektiğini belirtin** .

 Bu, dağıtım bildiriminde **Update** öğesinin **maximumAge** ve **Unit** özniteliklerinin ayarlanmasına benzer.

 Örneğin, her zaman uygulama çalıştığında, haftada bir defa veya ayda bir defa denetlemek isteyebilirsiniz. Ağ bağlantısı belirtilen zamanda mevcut değilse, güncelleştirme denetimi uygulamanın sonraki açılışında gerçekleştirilir.

## <a name="provide-a-user-interface-for-updates"></a>Güncelleştirmeler için bir kullanıcı arabirimi sağlama
 Bu stratejiyi kullanırken, uygulama geliştiricisi kullanıcıya ne zaman veya ne sıklıkta uygulama güncelleştirmeleri denetlensin seçeneği imkanı veren bir kullanıcı arayüzü sağlar. Örneğin, "Güncelleştirmeleri Şimdi Denetle" komutu veya dört farklı güncelleştirme aralığı içeren bir "Güncelleştirme Ayarları" iletişim kutusu sağlayabilirsiniz. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Dağıtım API 'leri, kendi güncelleştirme Kullanıcı arabiriminizi programlamak için bir çerçeve sağlar. Daha fazla bilgi için bkz <xref:System.Deployment.Application> . ad alanı.

 Uygulamanız kendi güncelleştirme mantığını denetlemek için dağıtım API'leri kullanıyorsa, aşağıdaki bölümde "Güncelleştirme Denetimini Engelleme"de anlatıldığı gibi güncelleştirme denetimini engellemelisiniz.

 Bu strateji, en iyi farklı kullanıcılar için farklı güncelleştirme stratejileri gerektiğinde çalışır.

## <a name="block-update-checking"></a>Güncelleştirme denetimini engelle
 Uygulamanızın güncelleştirme yapmasını tamamen engellemeniz mümkündür. Örneğin, hiçbir zaman güncelleştirilmemiş basit bir uygulamanız olabilir, ancak dağıtımın sağladığı yükleme kolaylığından yararlanmak istiyorsunuz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Ayrıca, uygulamanız kendi güncelleştirmelerini gerçekleştirmek için dağıtım API 'Leri kullanıyorsa, güncelleştirme denetimini de engellemeniz gerekir. Bu konunun önceki kısımlarında yer olarak "güncelleştirmeler için bir kullanıcı arabirimi sağlayın" bölümüne bakın.

 Güncelleştirme denetimini engellemek için uygulama güncelleştirmeleri Iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gerekir** onay kutusunu temizleyin.

 Ayrıca, etiketi dağıtım bildiriminden kaldırarak güncelleştirme denetimini engelleyebilirsiniz `<Subscription>` .

## <a name="permission-elevation-and-updates"></a>İzin yükseltme ve güncelleştirme
 Bir uygulamanın yeni bir sürümü [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önceki sürümden çalıştırmak için daha yüksek bir güven düzeyi gerektiriyorsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanıcıya, uygulamanın bu daha yüksek güven düzeyine verilmesini isteyip istemediğini sorar. Kullanıcı daha yüksek güven düzeyi vermeyi reddederse, güncelleştirme yüklenmez. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir sonraki yeniden başlatıldığında kullanıcıdan uygulamayı yeniden yüklemesi istenir. Bu noktada kullanıcı daha yüksek güven düzeyi verilmesini reddedip güncelleştirme gerekli değil şeklinde işaretlenirse, uygulamanın eski sürümü çalışacaktır. Ancak güncelleştirme gerekli ise, uygulama kullanıcı daha yüksek güven düzeyini kabul edene kadar çalışmaz.

 Güvenilir Uygulama Dağıtımı kullanıyorsanız, güven düzeyleri için hiçbir uyarı ile karşılaşmazsınız. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).

## <a name="see-also"></a>Ayrıca bkz.
 \<xref:System.Deployment.Application>
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulama güncelleştirmelerini nasıl gerçekleştirir](../deployment/how-clickonce-performs-application-updates.md)
- [Nasıl yapılır: ClickOnce uygulaması için güncelleştirmeleri yönetme](../deployment/how-to-manage-updates-for-a-clickonce-application.md)
