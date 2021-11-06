---
title: Bağlı hizmetler
description: Visual Studio Azure hizmetlerine nasıl bağlantı ekleyebileceğiniz hakkında bilgi edinin
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: overview
ms.date: 10/19/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2470c410eb2fff1da54343b139b80dc93f2c37a1
ms.sourcegitcommit: 32fa8ec0b469a7a9a87de25ff769d8d21d9f30d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2021
ms.locfileid: "131898150"
---
# <a name="overview-connected-services"></a>Genel Bakış: bağlı hizmetler

bağlı hizmetler, uygulamanızı aşağıdakilere bağlamanıza yardımcı olan Visual Studio bir araç koleksiyonudur:

* Azure hizmetleri
* Openapı uç noktaları
* gRPC (uzak yordam çağrısı) uç noktaları
* Windows Communication Foundation (WCF) uç noktaları

Çözüm Gezgini ' de **bağlı hizmetler** düğümüne sağ tıklayıp **bağlı hizmetleri Yönet**' i seçin.

Desteklenen proje türleri hizmet türüne göre farklılık gösterir. Listelenen seçimlerde proje türüne uygulanan seçenekleri görürsünüz.

## <a name="connect-your-app-to-grpc-openapi-and-wcf-endpoints"></a>uygulamanızı grpc, openapı ve WCF uç noktalarına Bağlan

Uygulamanızı aşağıdaki hizmetlerden birine bağlamak için bağlı hizmetleri kullanın:

| Name | ASP.NET Bağlantısının | Description |
|-|-|-|
| [Openapı](https://github.com/OAI/OpenAPI-Specification) uç noktaları | [openapı ile ASP.NET Core uygulamaları geliştirme](/aspnet/core/web-api/Microsoft.dotnet-openapi) | Bilgisayar tarafından okunabilen ve okunabilir biçimdeki bir hizmetin yeteneklerini açıklamak için standart bir biçim. |
| [GRPC](https://grpc.io/docs/) uç noktaları | [.NET 'teki gRPC hizmetlerine giriş](/aspnet/core/grpc/) | Açık kaynaklı, gerçek zamanlı bir yordam hizmeti çağırma. |
| [WCF](/dotnet/framework/wcf/) uç noktaları | yok | dağıtılmış bir hizmetler ağıyla programlamayı destekleyen .NET Framework bir çözüm. |

Visual Studio, iletişimi kolaylaştırmak için gerekli istemci veya sunucu kodunu oluşturacaktır.

## <a name="connect-your-app-azure-services"></a>uygulamanızın Azure hizmetlerini Bağlan

Uygulamanızı canlı Azure hizmetleri öykünücülerine ve diğer yerel diğer alternatifleri Azure hizmetlerine bağlamak için bağlı hizmetleri kullanın. Visual Studio şu anda şunları desteklemektedir:

| Ad | Açıklama |
| - | - |
| [Azure Depolama](/azure/storage) | Blob, tablo, kuyruk, disk desteği olan ölçeklenebilir bulut depolaması. |
| [Azure SignalR Hizmeti](/azure/azure-signalr/signalr-overview) | HTTP üzerinden gerçek zamanlı Web işlevselliği. |
| [Azure Key Vault](/azure/key-vault/general/overview) | Azure uygulamalarınız tarafından kullanılan şifreleme anahtarları ve diğer gizli dizileri için güvenli bulut depolaması. |
| [Azure SQL Veritabanı](/azure/azure-sql) | bulutta barındırılan SQL veritabanı. |
| [Redis için Azure Önbelleği](/azure/azure-cache-for-redis/cache-overview)| Redsıs yazılımını temel alan bellek içi veri deposu. |
| [Azure Cosmos DB](/azure/cosmos-db/introduction) | Modern uygulama geliştirmesi için tam olarak yönetilen bir NoSQL veritabanı.| 
| [Azure Microsoft Identity platformu](/azure/active-directory/develop/v2-overview) | Microsoft kimlikleri ve sosyal hesaplar ile kimlik doğrulama. |

> [!NOTE]
> Yayımlama kullanarak uygulamanızı Azure VM 'Leri, Azure App Service, Azure Işlevleri ve Azure Container Registry gibi Azure barındırma hizmetleri 'ne dağıtabilirsiniz

## <a name="support-for-azure-emulators-and-local-alternatives"></a>Azure öykünücüleri ve yerel alternatifler için destek

Visual Studio, yerel olarak öykündüğü hizmetlerden buluta çalışan hizmetlere geçişi kolaylaştırarak Azure uygulamalarını yerel olarak geliştirmeyi kolaylaştırır. Uygulamanızı yerel öykünücülere ve diğer yerel diğer alternatifleri Azure hizmetlerine bağlamak için bağlı hizmetleri kullanabilirsiniz. Visual Studio şu anda şunları desteklemektedir:

| Ad | Açıklama |
| - | - |
| [Azure Storage Öykünücüsü](/azure/storage/common/storage-use-azurite?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&tabs=visual-studio) | azurite, yerel makinenizde çalışan bir Azure Depolama öykünücüsüne sahiptir. |
| [Application Insights SDK](/azure/azure-monitor/app/app-insights-overview) | Application Insights hizmeti için yerel mod.  |
| [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb) | Azure SQL Veritabanı için yerel alternatif |
| [Gizlilikler. JSON](/aspnet/core/security/app-secrets?tabs=windows) | Key Vault için yerel alternatif |

## <a name="containers"></a>Kapsayıcılar

Bağlı hizmetler, bir kapsayıcıda yerel olarak Azure hizmetleri öykünmesi yapan uygulama bağımlılıklarını çalıştırmanıza yardımcı olabilir. yerel olarak kapsayıcıda azurite adlı Azure Depolama öykünücüsünü çalıştırabilirsiniz. Redsıs için Azure önbelleğine öykünmek üzere yerel olarak bir kapsayıcıda Redsıs 'i de çalıştırabilirsiniz.

## <a name="how-it-works"></a>Nasıl çalışır?

Visual Studio *servicedependencies. json* ve *servicedependencies. local. json* adlı özellikler altında Çözüm Gezgini görünür iki yeni dosya oluşturur. Bu dosyaların her ikisi de herhangi bir gizli dizi içermediği için iade etme güvendedir.

Visual Studio ayrıca, varsayılan olarak Çözüm Gezgini görünmeyen *servicedependencies. local. json. user* adlı bir dosya oluşturur. Bu dosya, gizli olarak değerlendirilen bilgiler içerir (örneğin, Azure 'da kaynak kimlikleri) ve bunu iade etmenizi önermeyiz.

