---
title: ClickOnce Uygulamalarını İstifa Etmeden Test ve Üretim Sunucuları Için Dağıtma | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395379"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Sınama ve Üretim Sunucuları için Teslim Etmeden ClickOnce Uygulamaları Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, .NET Framework sürüm 3.5'te tanıtılan ve ClickOnce uygulamalarını clickonce bildirimlerini yeniden imzalamadan veya değiştirmeden birden çok ağ noktasından dağıtımını sağlayan ClickOnce'nin yeni bir özelliğini tartışır.  
  
> [!NOTE]
> İstifa, uygulamaların yeni sürümlerini dağıtmak için hala tercih edilen yöntemdir. Mümkün olduğunda, istifa yöntemini kullanın. Daha fazla bilgi için [Mage.exe (Manifest Generation and Düzenleme Aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)bakın.  
  
 Üçüncü taraf geliştiriciler ve ISV'ler bu özelliği kabul ederek müşterilerinin uygulamalarını güncelleştirmelerini kolaylaştırır. Bu özellik aşağıdaki durumlarda kullanılabilir:  
  
- Bir uygulamayı güncellerken, uygulamanın ilk yüklemesini değil.  
  
- Bir bilgisayarda uygulamanın yalnızca bir yapılandırması olduğunda. Örneğin, bir uygulama iki farklı veritabanını işaret etmek üzere yapılandırılırsa, bu özelliği kullanamazsınız.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>DağıtımSağlayıcı'yı Dağıtım Bildirimlerinden Hariç  
 .NET Framework 2.0 ve .NET Framework 3.0'da, çevrimdışı kullanılabilirlik için sisteme yüklenen `deploymentProvider` herhangi bir ClickOnce uygulaması, dağıtım bildiriminde bir belirtmelidir. Genellikle `deploymentProvider` güncelleştirme konumu olarak adlandırılır; ClickOnce'nin uygulama güncelleştirmelerini denetleyeceği yerdir. Bu gereksinim, uygulama yayımcılarının dağıtımlarını imzalama gereksinimiyle birleştiğinde, bir şirketin clickonce uygulamasını bir satıcıdan veya diğer üçüncü taraflardan güncelleştirmesini zorlaştırdı. Ayrıca, aynı ağüzerinde birden çok konumdan aynı uygulamayı dağıtmak daha zor hale getirir.  
  
 .NET Framework 3.5'te ClickOnce'de yapılan değişikliklerle, üçüncü bir tarafın başka bir kuruluşa ClickOnce uygulaması sağlaması mümkündür ve bu uygulama daha sonra uygulamayı kendi ağında dağıtabilir.  
  
 Bu özellikten yararlanabilmek için ClickOnce uygulamalarının `deploymentProvider` geliştiricilerinin dağıtım bildirimlerini hariç tutmaları gerekir. Bu, Mage.exe ile dağıtım bildirimleri oluştururken `-providerUrl` bağımsız değişkeni dışlamak veya MageUI.exe ile dağıtım bildirimleri oluşturuyorsanız Uygulama **Bildirimi** sekmesindeki Başlat **Konumu** metin kutusunun boş bırakıldığından emin olmak anlamına gelir.  
  
## <a name="deploymentprovider-and-application-updates"></a>dağıtımSağlayıcı ve Uygulama Güncellemeleri  
 .NET Framework 3.5'ten başlayarak, hem `deploymentProvider` çevrimiçi hem de çevrimdışı kullanım için clickonce uygulamasını dağıtmak için artık dağıtım bildiriminizde bir uygulama belirtmeniz gerekmeyecektir. Bu, dağıtımı kendiniz paketlemeniz ve imzalamanız gereken, ancak diğer şirketlerin uygulamayı ağları üzerinden dağıtmasına izin verme niz gereken senaryoyu destekler.  
  
 Unutulmaması gereken önemli nokta, etiketi `deploymentProvider` yeniden içeren `deploymentProvider` bir güncelleştirme sevk edene kadar, a'yı dışlayan uygulamaların güncelleştirmeler sırasında yükleme konumlarını değiştiremeyeceğidir.  
  
 Bu noktayı açıklığa kavuşturmak için iki örnek verilmiştir. İlk örnekte, etiketi olmayan `deploymentProvider` bir ClickOnce uygulaması yayımlarsınız ve kullanıcılardan bunu ' dan yüklemelerini `http://www.adatum.com/MyApplication/`istersiniz. Uygulamanın bir sonraki güncelleştirmesini yayımlamaya karar `http://subdomain.adatum.com/MyApplication/`verirseniz, bunu içinde bulunan dağıtım bildiriminde belirtmenizin bir yolu `http://www.adatum.com/MyApplication/`yoktur. İki şeyden birini yapabilirsiniz:  
  
- Kullanıcılarınıza önceki sürümü kaldırmalarını ve yeni sürümü yeni konumdan yüklemelerini söyleyin.  
  
- Bir `http://www.adatum.com/MyApplication/` `deploymentProvider` işaret içeren bir güncelleştirme `http://www.adatum.com/MyApplication/`ekleyin. Daha sonra işaret ederek `deploymentProvider` başka `http://subdomain.adatum.com/MyApplication/`bir güncelleştirme yayımlayın.  
  
  İkinci örnekte, belirten `deploymentProvider`bir ClickOnce uygulaması yayımlarsınız ve ardından kaldırmaya karar verirsiniz. İstemlere indirilmeyen `deploymentProvider` yeni sürüm indirildikten sonra, uygulamanızın geri yüklenmiş `deploymentProvider` bir sürümünü yayımlayana kadar güncelleştirmeler için kullanılan yolu yeniden yönlendiremeyeceksiniz. İlk örnekte olduğu `deploymentProvider` gibi, başlangıçta geçerli güncelleştirme konumunuzu değil, yeni konumunuzu işaret etmelidir. Bu durumda, bir `deploymentProvider` `http://subdomain.adatum.com/MyApplication/`"bu" anlamına gelen bir eklemeye çalışırsanız, bir sonraki güncelleştirme başarısız olur.  
  
## <a name="creating-a-deployment"></a>Dağıtım Oluşturma  
 Farklı ağ konumlarından dağıtılabilen dağıtımlar oluşturma konusunda adım adım kılavuz [için, Walkthrough: Yeniden İmzalama Gerektirmeyen ve Marka Oluşturma Bilgilerini Koruyan Bir ClickOnce Uygulamasını El Ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)' ya bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mage.exe (Manifesto Oluşturma ve Düzenleme Aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifesto Oluşturma ve Düzenleme Aracı, Grafik İstemci)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
