---
title: Visual Studio'da Bağlı Deneyimler
description: Bağlı bir deneyim, istemci makineden İnternet'e bağlanır ve müşteriye bir hizmet sağlar.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 0a54ddd3bdc547d3a6c2fce66696851f634bc6a5
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534339"
---
# <a name="connected-experiences-in-visual-studio"></a>**Visual Studio'de bağlantılı deneyimler** #

Visual Studio, daha etkili bir şekilde kodlaymanız için tasarlanmış istemci yazılım uygulamalarından ve bağlı deneyimlerden oluşur. Bir [NuGet](/nuget/consume-packages/install-use-packages-visual-studio) güncelleştirme, [IntelliCode](/visualstudio/intellicode/overview) önerisini seçme ve Live Share aracılığıyla başka [bir geliştiriciyle işbirliği yapmak,](/visualstudio/liveshare/quickstart/share) bağlantılı deneyimlere örnek olarak verilmiştir. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Bu bağlı deneyimlerin kullanılabilir olup olmadığını seçme ##

Hangi bağlı deneyimlerin kullan biri olduğunu seçebilirsiniz. Belirli bağlı deneyimlerin kullanımı, euLA ile ilgili farklı ve ek koşullarla Visual Studio gerektirir. Bu deneyimler Microsoft'a ait çevrimiçi hizmetler ve/veya üçüncü tarafların sahip olduğu hizmetler olabilir. Örneğin, GitHub bağlı deneyimler kullanırken, [GitHub](https://docs.github.com/github/site-policy/github-privacy-statement) Gizlilik Bildirimi [ve GitHub](https://docs.github.com/github/site-policy/github-terms-of-service)Hizmet Koşulları , [GitHub](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)Kurumsal Hizmet Koşulları ve/veya Ek Ürün [Koşulları](https://docs.github.com/github/site-policy/github-additional-product-terms) geçerli olur. Bir Sorun [Bildirersanız,](../how-to-report-a-problem-with-visual-studio.md)Microsoft Kullanım [Koşulları'nın ve Microsoft Gizlilik Bildirimi'nin](https://www.microsoft.com/legal/terms-of-use) kabul [edersiniz.](https://privacy.microsoft.com/en-us/privacystatement) NuGet hizmetini kullanıyorsanız, NuGet Kullanım Koşulları'NuGet Microsoft Gizlilik [](https://www.nuget.org/policies/Terms) [Bildirimi'ne karar verirsiniz.](https://privacy.microsoft.com/en-us/privacystatement) 

Yükleme ve yükleme [Visual Studio, isteğe bağlı olarak yüklemek için iş yüklerini ve bileşenleri seçebilirsiniz.](../../install/install-visual-studio.md) İş yükleri ve bileşenler, işlevlerine bağlı olarak üçüncü taraf yazılımlarından faydalanarak bağlı deneyimleri etkinleştirebilir. Örneğin, Azure [geliştirme iş yükünü indirmek bulut uygulamalarınızı Azure'da yayımlamanıza olanak sağlar.](https://visualstudio.microsoft.com/vs/features/azure/) Yükleme seçimlerinizi temel alarak, bağlı deneyimlere bağlanmak, yapılandırmak ve kullanmak için Araçlar ve Seçenekler menüsünü de kullanabilirsiniz. Örneğin, bir sunucuya bağlanabilirsiniz, Azure Hizmetleri kimlik doğrulaması ekleyebilir veya IntelliCode veya LiveShare ayarlarını değiştirebilirsiniz.  

Hizmet bağlantısını etkinleştirmek veya devre dışı bırakmak [için de,](../../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md) kuruluş güvenlik duvarı ayarlarını kullanabilirsiniz. Uç nokta bağlantısının devre dışı bırakılmasının ilgili uç nokta özelliklerinin performansını olumsuz etkileyeceğini veya Visual Studio unutmayın. 

Son olarak Visual Studio Market, birinci veya üçüncü taraf bağlantılı deneyimleri etkinleştiren uzantılar sunar. Visual Studio Market, Visual Studio [Market Kullanım Koşulları ve](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) Microsoft Gizlilik [Bildirimi'ne bağlıdır.](https://privacy.microsoft.com/en-us/privacystatement) Her uzantı, belirli kullanım koşulları ve bu teklifle ilişkili gizlilik bildirimi için sözleşme gerektirir.  


## <a name="required-service-data"></a>Gerekli hizmet verileri ##

Gerekli hizmet verileri, bağlı deneyimin çalışmasıyla ilgili, temel alınan hizmetin güvenliğini sağlamak, güncel tutmak ve beklendiği gibi performans sağlamak için gereken bilgileri içerebilir. İçeriğinizi analiz etmek için IntelliCode gibi bağlı bir deneyim kullanmayı seçerseniz, modeliniz için seçtiğiniz kod da gönderilir ve size bağlı deneyimi sağlamak için işlenir. Gerekli hizmet verileri, bağlı bir deneyimin görevini gerçekleştirmek için ihtiyaç NuGet içerebilir. Belirli bir hizmeti kullanıp kullanmama konusunda seçim yapmak için gerekli hizmet verilerini yönetebilirsiniz. Bir hizmet kullansanız, gerekli hizmet verileri toplanmaz. 

Tanılama verileri, cihazınız üzerinde çalışan yazılımla ilişkili olduğundan, gerekli hizmet verileri tanılama verilerinden farklıdır. Tanılama verileri için Visual Studio Müşteri Deneyimini Geliştirme Programı [(VSCEIP)](../visual-studio-experience-improvement-program.md)hizmetine katılmayı tercih edersiniz, ancak bu ayar gerekli hizmet verisi gönderip gönderilmeyeceğini etkilemez. 

## <a name="diagnostic-data-collection"></a>Tanılama verileri toplama ##

Tanılama verileri, verileri güvenli Visual Studio güncel tutmak, sorunları algılamak, tanılamak ve düzeltmek ve ürün geliştirmeleri yapmak için kullanılır. Tanılama verileri toplanır ve kullanıcının cihazında Visual Studio hakkında Microsoft'a gönderilir.

Bu seçeneği devre dışı bırakmanız, isteğe bağlı tanılama verileri toplamayı geri kabul etmek değildir. Verilerin güvenli, güncel ve beklendiği gibi Visual Studio emin olmak için bazı tanılama verileri toplaması gerekir. Gerekli tanılama verisi toplama, VSCEIP'yi geri almayı geri almak sizin [seçiminiz tarafından etkilenmez.](../visual-studio-experience-improvement-program.md) 
