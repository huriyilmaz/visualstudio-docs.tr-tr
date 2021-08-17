---
title: ClickOnce uygulamalarını yeniden imzalama olmadan dağıtma
description: ClickOnce bildirimlerini yeniden imzalamadan veya değiştirmeden birden çok ağ konumundan ClickOnce uygulamaları dağıtma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: ca7c1e4e8e56708a529eb23f68b9ab7bc3e3530cdd0b39e4b358a3b435da3810
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435679"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>sınama ve üretim sunucuları için teslim etmeden ClickOnce uygulamaları dağıtma
bu makalede, ClickOnce bildirimlerini yeniden imzalamadan veya değiştirmeden birden çok ağ konumundan ClickOnce uygulamalarının dağıtımına izin veren .NET Framework sürüm 3,5 ' de tanıtılan ClickOnce bir özelliği açıklanır.

> [!NOTE]
> Çekilmeye devam etmek, uygulamaların yeni sürümlerini dağıtmak için tercih edilen yöntemdir. Mümkün olduğunda, çekilme yöntemini kullanın. daha fazla bilgi için bkz. [ *Mage.exe* (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Üçüncü taraf geliştiriciler ve ISV 'Ler bu özelliği kabul edebilir ve müşterilerinin uygulamalarını güncelleştirmesine daha kolay hale gelir. Bu özellik aşağıdaki durumlarda kullanılabilir:

- Bir uygulamayı güncelleştirirken, uygulamanın ilk yüklemesi için değil.

- Bir bilgisayarda uygulamanın yalnızca bir yapılandırması olduğunda. Örneğin, bir uygulama iki farklı veritabanına işaret etmek üzere yapılandırıldıysa, bu özelliği kullanamazsınız.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Dağıtım bildirimlerinden deploymentProvider 'ı hariç tut
 .NET Framework 2,0 ve .NET Framework 3,0 ' de, çevrimdışı kullanılabilirlik için sisteme yüklenen tüm ClickOnce uygulamalarının dağıtım bildiriminde bir listesi olmalıdır `deploymentProvider` . `deploymentProvider`genellikle güncelleştirme konumu olarak adlandırılır; ClickOnce uygulama güncelleştirmelerini denetlediği yerdir. bu gereksinim, uygulama yayımcılarının dağıtımlarını imzalamasını gerektiren bir şirketin bir satıcıdan veya diğer üçüncü taraflardan ClickOnce bir uygulamayı güncelleştirmesini zorlaştırıyordu. Aynı uygulamanın aynı ağdaki birden çok konumdan aynı uygulamayı dağıtmayı daha da zorlaştırır.

 .NET Framework 3,5 ' de ClickOnce yapılan değişikliklerle, üçüncü bir tarafın başka bir kuruluşa ClickOnce uygulama sağlaması olasıdır ve bu, uygulamayı kendi ağına dağıtabolabilir.

 bu özellikten yararlanabilmek için ClickOnce uygulamalarının geliştiricileri `deploymentProvider` dağıtım bildirimlerinden hariç tutmalıdır. Bu gereksinim, `-providerUrl` Mage.exe ile dağıtım bildirimleri oluştururken bağımsız değişkeni dışlamayabilmeniz gerektiği anlamına gelir. Ya da MageUI.exe ile dağıtım bildirimleri oluşturuyorsanız, **uygulama bildirimi** sekmesindeki **başlatma konumu** metin kutusunun boş bırakıltığınızdan emin olmalısınız.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider ve uygulama güncelleştirmeleri
 .NET Framework 3,5 ' den başlayarak, `deploymentProvider` hem çevrimiçi hem de çevrimdışı kullanım için bir ClickOnce uygulaması dağıtmak amacıyla dağıtım bildiriminizde bir de belirtmeniz gerekmez. Bu değişiklik, dağıtımı kendiniz paketleyip imzalamanız gereken, ancak diğer şirketlerin uygulamayı ağları üzerinden dağıtmasına izin veren senaryoyu destekler.

 Anımsanması gereken önemli nokta, bir `deploymentProvider` yeniden etiketi içeren bir güncelleştirme sevk edene kadar, bir öğesini hariç tutma uygulamalarının güncelleştirme sırasında kendi yük konumlarını değiştirememesini sağlar `deploymentProvider` .

 Bu noktayı netleştirmek için iki örnek aşağıda verilmiştir. ilk örnekte, etiketi olmayan bir ClickOnce uygulaması yayımlarsınız `deploymentProvider` ve kullanıcılardan bunu yüklemesini isteyebilirsiniz `http://www.adatum.com/MyApplication/` . Uygulamanın bir sonraki güncelleştirmesini ' dan yayınlamak istiyorsanız `http://subdomain.adatum.com/MyApplication/` , bu, ' de bulunan dağıtım bildiriminde bunu belirtmenin bir yolu yoktur `http://www.adatum.com/MyApplication/` . İki işlemlerden birini yapabilirsiniz:

- Kullanıcılarınıza önceki sürümü kaldırmalarını söyleyin ve yeni konumdan yeni sürümü yükler.

- Üzerine işaret içeren bir güncelleştirme ekleyin `http://www.adatum.com/MyApplication/` `deploymentProvider` `http://www.adatum.com/MyApplication/` . Daha sonra, üzerine gelip daha sonra başka bir güncelleştirmeyi yayınlayın `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` .

  ikinci örnekte, öğesini belirten ClickOnce bir uygulama yayımlarsınız `deploymentProvider` ve sonra kaldırmaya karar verirsiniz. Yeni sürüm, `deploymentProvider` istemcilere indirildikten sonra, geri yüklenen uygulamanızın bir sürümünü bırakmadan güncelleştirmeler için kullanılan yolu yeniden yönlendiremezsiniz `deploymentProvider` . İlk örnekte olduğu gibi, `deploymentProvider` Başlangıçta yeni konumunuzu değil geçerli güncelleştirme konumunu işaret etmelidir. Bu durumda, öğesine başvuran bir eklemek için bir `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` sonraki güncelleştirme başarısız olur.

## <a name="create-a-deployment"></a>Dağıtım oluşturma
 farklı ağ konumlarından dağıtılabilecek dağıtımlar oluşturmaya yönelik adım adım yönergeler için bkz. [izlenecek yol: yeniden imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Ayrıca bkz.
- [*Mage.exe* (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Bildirim Oluşturma ve Düzenleme Aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
