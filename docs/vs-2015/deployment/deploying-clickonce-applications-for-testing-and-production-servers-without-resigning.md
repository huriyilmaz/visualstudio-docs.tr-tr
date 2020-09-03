---
title: Sınama ve üretim sunucuları Için teslim etmeden ClickOnce uygulamaları dağıtma | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395379"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Sınama ve Üretim Sunucuları için Teslim Etmeden ClickOnce Uygulamaları Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, ClickOnce bildirimlerinin yeniden imzalanmadan veya değiştirilmeden birden çok ağ konumundan ClickOnce uygulamalarının dağıtılmasını sağlayan .NET Framework sürüm 3,5 ' de tanıtılan yeni bir ClickOnce özelliği ele alınmaktadır.  
  
> [!NOTE]
> Çekilmeye devam etmek, uygulamaların yeni sürümlerini dağıtmak için tercih edilen yöntemdir. Mümkün olduğunda, çekilme yöntemini kullanın. Daha fazla bilgi için bkz. [Mage.exe (bildirim oluşturma ve düzenleme aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Üçüncü taraf geliştiriciler ve ISV 'Ler bu özelliği kabul edebilir ve müşterilerinin uygulamalarını güncelleştirmesine daha kolay hale gelir. Bu özellik aşağıdaki durumlarda kullanılabilir:  
  
- Bir uygulamayı güncelleştirirken, uygulamanın ilk yüklemesi değil.  
  
- Bir bilgisayarda uygulamanın yalnızca bir yapılandırması olduğunda. Örneğin, bir uygulama iki farklı veritabanına işaret etmek üzere yapılandırıldıysa, bu özelliği kullanamazsınız.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Dağıtım bildirimlerinden deploymentProvider hariç  
 .NET Framework 2,0 ve .NET Framework 3,0 ' de, çevrimdışı kullanılabilirlik için sisteme yüklenen herhangi bir ClickOnce uygulaması, `deploymentProvider` dağıtım bildiriminde bir olarak belirtilmelidir. `deploymentProvider`Genellikle güncelleştirme konumu olarak adlandırılır; Bu, ClickOnce 'ın uygulama güncelleştirmelerini denetebileceği konumdur. Bu gereksinim, uygulama yayımcılarının dağıtımlarını imzalama gereksinimiyle birlikte kullanıldığında, bir şirketin bir ClickOnce uygulamasını bir satıcıdan veya diğer üçüncü tarafınızdan güncelleştirmesini zorlaştırıyordu. Aynı uygulamanın aynı ağdaki birden çok konumdan aynı uygulamayı dağıtmayı daha da zorlaştırır.  
  
 .NET Framework 3,5 ' de ClickOnce üzerinde yapılan değişikliklerle, üçüncü tarafın başka bir kuruluşa ClickOnce uygulaması sağlaması olasıdır ve bu da uygulamayı kendi ağına dağıtabolabilir.  
  
 Bu özelliğin avantajlarından yararlanabilmek için, ClickOnce uygulamalarının geliştiricileri dağıtım bildirimlerinden hariç tutmalıdır `deploymentProvider` . Bu, `-providerUrl` Mage.exe ile dağıtım bildirimleri oluşturduğunuzda bağımsız değişkeni hariç tutma veya MageUI.exe ile dağıtım bildirimleri oluşturuyorsanız **uygulama bildirimi** sekmesindeki **başlatma konumu** metin kutusunun boş bırakılması anlamına gelir.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider ve uygulama güncelleştirmeleri  
 .NET Framework 3,5 ' den başlayarak, `deploymentProvider` hem çevrimiçi hem de çevrimdışı kullanım için bir ClickOnce uygulaması dağıtmak amacıyla dağıtım bildiriminizde bir de belirtmeniz gerekmez. Bu, dağıtımı kendiniz paketleyip imzalamanız gereken, ancak diğer şirketlerin uygulamayı ağları üzerinden dağıtmasına izin veren senaryoyu destekler.  
  
 Anımsanacak anahtar noktası, bir `deploymentProvider` yeniden etiketi içeren bir güncelleştirme sevk edene kadar, bir öğesini hariç tutma uygulamalarının güncelleştirme sırasında kendi yük konumlarını değiştirememesini sağlar `deploymentProvider` .  
  
 Bu noktayı netleştirmek için iki örnek aşağıda verilmiştir. İlk örnekte, etiketi olmayan bir ClickOnce uygulaması yayımlarsınız `deploymentProvider` ve kullanıcılardan bunu yüklemesini isteyebilirsiniz `http://www.adatum.com/MyApplication/` . Uygulamanın bir sonraki güncelleştirmesini ' dan yayınlamak istiyorsanız `http://subdomain.adatum.com/MyApplication/` , bu, ' de bulunan dağıtım bildiriminde bunu belirtmenin bir yolu olmayacaktır `http://www.adatum.com/MyApplication/` . İki işlemlerden birini yapabilirsiniz:  
  
- Kullanıcılarınıza önceki sürümü kaldırmalarını söyleyin ve yeni konumdan yeni sürümü yükler.  
  
- Üzerine işaret içeren bir güncelleştirme ekleyin `http://www.adatum.com/MyApplication/` `deploymentProvider` `http://www.adatum.com/MyApplication/` . Daha sonra, üzerine gelip daha sonra başka bir güncelleştirmeyi yayınlayın `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` .  
  
  İkinci örnekte, öğesini belirten bir ClickOnce uygulaması yayımlarsınız `deploymentProvider` ve daha sonra kaldırmaya karar verirsiniz. Yeni sürüm, `deploymentProvider` istemcilere indirilmeden sonra, geri yüklenen uygulamanızın bir sürümünü serbest bırakana kadar, güncelleştirmeler için kullanılan yolu yeniden yönlendiremeyeceksiniz `deploymentProvider` . İlk örnekte olduğu gibi, `deploymentProvider` Başlangıçta yeni konumunuzu değil geçerli güncelleştirme konumunu işaret etmelidir. Bu durumda, öğesine başvuran bir eklemek için bir `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` sonraki güncelleştirme başarısız olur.  
  
## <a name="creating-a-deployment"></a>Dağıtım oluşturma  
 Farklı ağ konumlarından dağıtılabilecek dağıtımlar oluşturmaya yönelik adım adım yönergeler için bkz. [Izlenecek yol: yeniden Imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını El Ile dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, grafik Istemci)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
