---
title: Yeniden ClickOnce olmadan uygulama dağıtma
description: Bildirimleri yeniden imzalamadan ClickOnce değiştirmeden birden çok ağ konumdan uygulama dağıtma ClickOnce öğrenin.
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
ms.openlocfilehash: 19eb91f9becdeeddbf5f5436a4f0b3b7da59da77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160861"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Yeniden ClickOnce olmadan test ve üretim sunucuları için uygulama dağıtma
Bu makalede, .NET Framework sürüm 3.5'te tanıtan ve ClickOnce uygulamalarının birden çok ağ konumdan yeniden imzalamadan veya bildirimlerini değiştirmeden dağıtımını sağlayan ClickOnce bir ClickOnce özelliği açıklanmıştır.

> [!NOTE]
> Yeniden atama, uygulamaların yeni sürümlerini dağıtmak için tercih edilen yöntemdir. Mümkün olduğunda, yeniden atama yöntemini kullanın. Daha fazla bilgi için [ *bkz.Mage.exe* (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Üçüncü taraf geliştiriciler ve ISV'ler bu özelliği tercih eder ve bu da müşterilerinin uygulamalarını güncelleştirmesini kolaylaştırır. Bu özellik aşağıdaki durumlarda kullanılabilir:

- Bir uygulamanın ilk yüklemesi için değil, bir uygulamayı güncelleştiriyor.

- Bilgisayarda uygulamanın yalnızca bir yapılandırması olduğunda. Örneğin, bir uygulama iki farklı veritabanına işaret etmek üzere yapılandırılmışsa bu özelliği kullanılamaz.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>DeploymentProvider'ın dağıtım bildirimlerini dışlama
 .NET Framework 2.0 ve .NET Framework 3.0'da, çevrimdışı kullanılabilirlik için sistemde yüklü olan tüm ClickOnce uygulamanın dağıtım bildiriminde bir `deploymentProvider` listesi olması gerekir. `deploymentProvider`genellikle güncelleştirme konumu olarak adlandırılır; uygulama güncelleştirmelerini denetlerken ClickOnce konumu olur. Bu gereksinim, uygulama yayımcılarının dağıtımlarını imzalama gereksinimiyle birlikte, bir şirketin satıcıdan veya diğer üçüncü taraftan ClickOnce bir uygulama güncelleştirmesini zorlaştırdı. Ayrıca aynı uygulamayı aynı ağ üzerinde birden çok konumdan dağıtmayı da zorlaştırıyor.

 ClickOnce 3.5'te .NET Framework'de yapılan değişikliklerle birlikte, üçüncü taraf başka bir kuruluşa bir ClickOnce uygulaması sağlamak ve daha sonra uygulamayı kendi ağına dağıtabilirsiniz.

 Bu özellikten yararlanmak için, uygulama geliştiricilerinin ClickOnce bildirimlerini `deploymentProvider` dışlamaları gerekir. Bu gereksinim, dağıtım bildirimleri oluşturmak için `-providerUrl` bağımsız değişkeni dışlamanız gerektiğini Mage.exe. Öte ya da dağıtım bildirimleri MageUI.exe, Uygulama Bildirimi sekmesindeki Konumu  Başlat metin kutusunun  boş bırakıla olduğundan emin olun.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider ve uygulama güncelleştirmeleri
 .NET Framework 3.5'den başlayarak, hem çevrimiçi hem de çevrimdışı kullanım için bir ClickOnce uygulaması dağıtmak için dağıtım bildiriminde bir `deploymentProvider` belirtmenize gerek yoktur. Bu değişiklik, dağıtımı kendiniz paketleyip imzalamanız gereken ancak diğer şirketlerin uygulamayı ağları üzerinden dağıtmasına izin vermenizi sağlayan senaryoyu destekler.

 Anımsanacak önemli nokta, dışlanan uygulamaların, etiketi içeren bir güncelleştirmeyi yeniden gönderinceye kadar güncelleştirmeler sırasında yükleme `deploymentProvider` konumlarını `deploymentProvider` değiştiremeyecekleridir.

 Bu noktaya açıklık getirmek için iki örnek aşağıda verilmiştir. İlk örnekte, etiketi ClickOnce bir uygulama yayımlayacak ve kullanıcılardan uygulamasını `deploymentProvider` 'den yüklemelerini isteyebilirsiniz. `http://www.adatum.com/MyApplication/` uygulamasının bir sonraki güncelleştirmesini 'den yayımlamak istediğinize karar verdiyebilirsiniz. Bunu içinde bulunan dağıtım bildiriminde `http://subdomain.adatum.com/MyApplication/` imzalamanın hiçbir yolu `http://www.adatum.com/MyApplication/` yoktur. İki şeyden birini yapabiliriz:

- Kullanıcılarınıza önceki sürümü kaldırmalarını ve yeni sürümü yeni konumdan yüklemelerini söyleyin.

- üzerine işaret içeren `http://www.adatum.com/MyApplication/` bir `deploymentProvider` güncelleştirme dahil. `http://www.adatum.com/MyApplication/` Ardından, daha sonra üzerine işaret etmek için başka `deploymentProvider` bir güncelleştirme `http://subdomain.adatum.com/MyApplication/` yayımlar.

  İkinci örnekte, belirten bir ClickOnce uygulaması yayımlayacak ve `deploymentProvider` sonra kaldırmaya karar vereceksiniz. olmadan yeni sürüm istemcilere indirildikten sonra, uygulamanın geri yüklenen bir sürümünü yayınlaya kadar güncelleştirmeler `deploymentProvider` için kullanılan yolu yeniden yönlendirilemezsiniz. `deploymentProvider` İlk örnekte olduğu gibi, `deploymentProvider` yeni konumunuz değil, başlangıçta geçerli güncelleştirme konumunu işaret etmek gerekir. Bu durumda, 'a başvuran bir `deploymentProvider` eklemeye çalışırken `http://subdomain.adatum.com/MyApplication/` sonraki güncelleştirme başarısız olur.

## <a name="create-a-deployment"></a>Dağıtım oluşturma
 Farklı ağ konumlarından dağıtılabilir dağıtımlar oluşturma hakkında adım adım kılavuz için bkz. Adım adım kılavuz: Yeniden imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını el [ile dağıtma.](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)

## <a name="see-also"></a>Ayrıca bkz.
- [*Mage.exe* (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
