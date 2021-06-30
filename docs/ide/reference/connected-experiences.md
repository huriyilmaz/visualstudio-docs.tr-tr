---
title: Visual Studio 'da bağlı deneyimler
description: Bağlı bir deneyim, bir istemci makinesinden internet 'e bağlanır ve müşteriye bir hizmet sağlar.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 246b2496248cc66c180c577fdd1f7a202609117d
ms.sourcegitcommit: 7393a37ce77c5b80312ce787baa060c91d41d959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113114795"
---
# <a name="connected-experiences-in-visual-studio"></a>**Visual Studio 'da bağlı deneyimler** #

Visual Studio, daha verimli bir şekilde kod getirmenize olanak tanımak için tasarlanan istemci yazılım uygulamalarından ve bağlı deneyimlerden oluşur. Bir [NuGet](/nuget/consume-packages/install-use-packages-visual-studio) paketini güncelleştirme, [ıntellicode](/visualstudio/intellicode/overview)önerisi seçme ve [live share](/visualstudio/liveshare/quickstart/share) aracılığıyla başka bir geliştiriciyle işbirliği yapma, bağlı deneyimlere örnektir. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Bu bağlantı deneyimlerinin kullanılabilir olup olmadığını seçin ##

Hangi bağlı deneyimleri kullanacağınızı seçebilirsiniz. Belirli bağlı deneyimlerin kullanımı, Visual Studio EULA 'ya farklı ve ek koşullara yönelik anlaşma gerektirir. Bu deneyimler, Microsoft 'a ait çevrimiçi hizmetler ve/veya üçüncü taraflara ait hizmetler olabilir. Örneğin, GitHub bağlantılı deneyimleri kullandığınızda [GitHub gizlilik bildirimi](https://docs.github.com/github/site-policy/github-privacy-statement) ve [GitHub hizmet koşulları](https://docs.github.com/github/site-policy/github-terms-of-service), [GitHub kurumsal hizmet koşulları](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)ve/veya [ek ürün koşulları](https://docs.github.com/github/site-policy/github-additional-product-terms) uygulanır. [Bir sorun Raporlıyorsanız](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) [Microsoft kullanım koşulları](https://www.microsoft.com/legal/terms-of-use) ' nı ve [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/en-us/privacystatement)' ni kabul etmiş olursunuz. NuGet hizmetini kullanıyorsanız, [NuGet kullanım koşullarını](https://www.nuget.org/policies/Terms) ve [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/en-us/privacystatement)' ni kabul etmiş olursunuz. 

Visual Studio 'Yu yüklediğinizde, [isteğe bağlı olarak yüklenecek iş yüklerini ve bileşenleri seçebilirsiniz](/visualstudio/install/install-visual-studio). İş yükleri ve bileşenler, üçüncü taraflardan yararlanabilir ve işlevlerine bağlı olarak bağlı deneyimleri etkinleştirebilir. Örneğin, [Azure geliştirme iş yükünün indirilmesi, bulut uygulamalarınızı Azure 'da yayımlamanıza olanak sağlar](https://visualstudio.microsoft.com/vs/features/azure/). Yükleme seçimlerinize bağlı olarak, bağlanmak, yapılandırmak ve bağlı deneyimleri kullanmak için araçlar ve Seçenekler menüsünü de kullanabilirsiniz. Örneğin, bir sunucuya bağlanabilir, Azure Hizmetleri kimlik doğrulaması ekleyebilir veya ıntellicode veya livesununununununununununununun  

Ayrıca, hizmetlerin bağlantısını etkinleştirmek veya devre dışı bırakmak için kuruluşunuzun [Güvenlik Duvarı ayarlarını](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) da kullanabilirsiniz. Bir uç nokta bağlantısının devre dışı bırakılması, ilgili Visual Studio özelliklerinin performansını olumsuz yönde etkileyebilir veya devre dışı bırakabileceğini unutmayın. 

Son olarak Visual Studio Market, birinci veya üçüncü taraf bağlantılı deneyimleri etkinleştirebilen uzantılar sunar. Visual Studio Market, [Visual Studio Market kullanım koşulları](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) ve [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/en-us/privacystatement)' ne tabidir. Her uzantı, bu teklifle ilişkili belirli kullanım koşulları ve gizlilik bildirimi için anlaşma gerektirir.  


## <a name="required-service-data"></a>Gerekli hizmet verileri ##

Gerekli hizmet verileri, temeldeki hizmeti güvenli bir şekilde korumak için gereken bağlı deneyimin işlemiyle ilgili bilgileri ve beklendiği gibi gerçekleştirmeyi içerebilir. İçeriğinizi analiz eden bir bağlı deneyim kullanmayı tercih ederseniz (örneğin, ıntellicode), modelinize seçtiğiniz kod, bağlantılı deneyim sağlamak için de gönderilir ve işlenir. Gerekli hizmet verileri, bir NuGet paketini güncelleştirmek için bağlı bir deneyim için gereken bilgileri de içerebilir. Belirli bir hizmeti kullanıp kullanmayacağınızı seçerek gerekli hizmet verilerini yönetebilirsiniz. Bir hizmet kullanmıyorsanız, gerekli hizmet verisi toplanmaz. 

Tanılama verileri, cihazınızda çalışan yazılımla ilişkili olduğundan, gerekli hizmet verileri tanılama verilerinden farklıdır. [Visual Studio müşteri deneyimini geliştirme programı (VSCEıP)](/visualstudio/ide/visual-studio-experience-improvement-program)uygulamasına katılıp katılmayacağınızı tercih ettiğiniz, tanılama verileri için gizlilik ayarlarını denetler, ancak bu ayar gerekli hizmet verilerinin gönderilip gönderilmeyeceğini etkilemez. 

## <a name="diagnostic-data-collection"></a>Tanılama verileri toplama ##

Tanılama verileri, Visual Studio 'Yu güvenli ve güncel tutmak, sorunları algılamak, tanılamak ve onarmak ve ayrıca ürün geliştirmeleri yapmak için kullanılır. Tanılama verileri toplanır ve kullanıcının cihazında çalışan Visual Studio istemci yazılımı hakkında Microsoft 'a gönderilir.

Bunu devre dışı bırakırsanız, isteğe bağlı tanılama veri toplamayı devre dışı olursunuz. Visual Studio 'Nun güvenli olduğundan, güncel olduğundan ve beklendiği gibi çalıştığından emin olmak için bazı tanılama verileri koleksiyonu gerekir. Gerekli tanılama veri toplama, [Vsceıp](/visualstudio/ide/visual-studio-experience-improvement-program)'i devre dışı bırakmak için seçiminizden etkilenmeyecektir. 
