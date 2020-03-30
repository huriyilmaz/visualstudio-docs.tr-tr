---
title: Yeniden imzalamadan ClickOnce uygulamalarını dağıtın
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395320"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>ClickOnce uygulamalarını istifa etmeden test ve üretim sunucuları için dağıtın
Bu makalede, ClickOnce'nin .NET Framework sürüm 3.5'te tanıtılan ve ClickOnce uygulamalarını yeniden imzalamadan veya değiştirmeden birden çok ağ noktasından dağıtımını sağlayan bir özellik açıklanmaktadır.

> [!NOTE]
> İstifa, uygulamaların yeni sürümlerini dağıtmak için hala tercih edilen yöntemdir. Mümkün olduğunda, istifa yöntemini kullanın. Daha fazla bilgi için [ *Mage.exe* (Manifest Generation and Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)bakın.

 Üçüncü taraf geliştiriciler ve ISV'ler bu özelliği tercih ederek müşterilerinin uygulamalarını güncelleştirmelerini kolaylaştırır. Bu özellik aşağıdaki durumlarda kullanılabilir:

- Bir uygulamayı güncellerken, bir uygulamanın ilk yüklemesi için değil.

- Bir bilgisayarda uygulamanın yalnızca bir yapılandırması olduğunda. Örneğin, bir uygulama iki farklı veritabanını işaret etmek üzere yapılandırılırsa, bu özelliği kullanamazsınız.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Dağıtım Sağlayıcı'yı dağıtım bildirimlerinden hariç tutma
 .NET Framework 2.0 ve .NET Framework 3.0'da, çevrimdışı kullanılabilirlik için sisteme yüklenen `deploymentProvider` herhangi bir ClickOnce uygulaması, dağıtım bildiriminde bir listelenmelidir. Genellikle `deploymentProvider` güncelleştirme konumu olarak adlandırılır; clickonce'nin uygulama güncelleştirmelerini denetlediği yerdir. Bu gereksinim, uygulama yayımcılarının dağıtımlarını imzalama gereksinimiyle birlikte, bir şirketin clickonce uygulamasını bir satıcıdan veya diğer üçüncü taraflardan güncelleştirmesini zorlaştırdı. Ayrıca, aynı ağüzerinde birden çok konumdan aynı uygulamayı dağıtmak daha zor hale getirir.

 .NET Framework 3.5'te ClickOnce'de yapılan değişikliklerle, üçüncü bir tarafın başka bir kuruluşa ClickOnce uygulaması sağlaması mümkündür ve bu uygulama daha sonra uygulamayı kendi ağında dağıtabilir.

 Bu özellikten yararlanabilmek için ClickOnce uygulamalarının `deploymentProvider` geliştiricilerinin dağıtım bildirimlerini hariç tutmaları gerekir. Bu gereksinim, Mage.exe ile dağıtım bildirimleri oluştururken `-providerUrl` bağımsız değişkeni hariç tutmanız gerektiği anlamına gelir. Veya MageUI.exe ile dağıtım bildirimleri oluşturuyorsanız, **Uygulama Bildirimi** sekmesindeki **Başlat Konumu** metin kutusunun boş bırakıldığından emin olmalısınız.

## <a name="deploymentprovider-and-application-updates"></a>dağıtımSağlayıcı ve uygulama güncellemeleri
 .NET Framework 3.5'ten başlayarak, hem `deploymentProvider` çevrimiçi hem de çevrimdışı kullanım için clickonce uygulamasını dağıtmak için artık dağıtım bildiriminizde bir uygulama belirtmeniz gerekmeyecektir. Bu değişiklik, dağıtımı kendiniz paketlemeniz ve imzalamanız gereken, ancak diğer şirketlerin uygulamayı ağları üzerinden dağıtmasına izin veren senaryoyu destekler.

 Unutulmaması gereken önemli nokta, etiketi `deploymentProvider` yeniden içeren `deploymentProvider` bir güncelleştirme sevk edene kadar, a'yı dışlayan uygulamaların güncelleştirmeler sırasında yükleme konumlarını değiştiremeyeceğidir.

 Bu noktayı açıklığa kavuşturmak için iki örnek verilmiştir. İlk örnekte, etiketi olmayan `deploymentProvider` bir ClickOnce uygulaması yayımlarsınız ve kullanıcılardan bunu ' dan yüklemelerini `http://www.adatum.com/MyApplication/`istersiniz. Uygulamanın bir sonraki güncelleştirmesini yayımlamaya karar `http://subdomain.adatum.com/MyApplication/`verirseniz, bunu içinde bulunan dağıtım bildiriminde belirtmenizin bir yolu `http://www.adatum.com/MyApplication/`yoktur. İki şeyden birini yapabilirsiniz:

- Kullanıcılarınıza önceki sürümü kaldırmalarını ve yeni sürümü yeni konumdan yüklemelerini söyleyin.

- Bir `http://www.adatum.com/MyApplication/` `deploymentProvider` işaret içeren bir güncelleştirme `http://www.adatum.com/MyApplication/`ekleyin. Daha sonra işaret ederek `deploymentProvider` başka `http://subdomain.adatum.com/MyApplication/`bir güncelleştirme yayımlayın.

  İkinci örnekte, belirten `deploymentProvider`bir ClickOnce uygulaması yayımlarsınız ve ardından kaldırmaya karar verirsiniz. Yeni sürüm istemcilere `deploymentProvider` indirildikten sonra, uygulamanızın geri yüklenmiş `deploymentProvider` bir sürümünü yayımlayana kadar güncelleştirmeler için kullanılan yolu yeniden yönlendiremezsiniz. İlk örnekte olduğu `deploymentProvider` gibi, başlangıçta geçerli güncelleştirme konumunuzu değil, yeni konumunuzu işaret etmelidir. Bu durumda, bir başvuru da `deploymentProvider` eklemeyi `http://subdomain.adatum.com/MyApplication/`denerseniz, sonraki güncelleştirme başarısız olur.

## <a name="create-a-deployment"></a>Dağıtım oluşturma
 Farklı ağ konumlarından dağıtılabilen dağıtımlar oluşturma konusunda adım adım kılavuz için [Walkthrough: Yeniden imzalamayı gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını el ile dağıtın.](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)

## <a name="see-also"></a>Ayrıca bkz.
- [*Mage.exe* (Manifesto Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Manifesto Oluşturma ve Düzenleme Aracı, Grafik İstemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
