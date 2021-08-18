---
title: MSBuild APı | Microsoft Docs
description: programınızın derleme gerçekleştirebilmesi ve proje incelemesi için MSBuild ortak apı yüzeyi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5ab75ae34fbea3b8423e074b3c5120459c681169
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115778"
---
# <a name="use-the-msbuild-api"></a>MSBuild apı 'sini kullanma

MSBuild, programınızın derleme gerçekleştirmesini ve proje incelemenizi sağlamak için genel bir apı yüzeyi sağlar. MSBuild apı 'lerinin son sürümleri aşağıdaki NuGet paketlerinde bulunabilir:

| Paket adı | Açıklama |
| ------------ | ----------- |
| [Microsoft. Build](https://www.nuget.org/packages/Microsoft.Build) | MSBuild projeleri oluşturmak, düzenlemek ve değerlendirmek için kullanılan Microsoft. Build derlemesini içerir.|
| [Microsoft. Build. Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| diğer MSBuild derlemeleri tarafından kullanılan ortak MSBuild framework derlemesini içerir. |
| [Microsoft. Build. Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | MSBuild 'ın tamamen yürütülebilir bir kopyasını sunar. Bu pakete yalnızca uygulamanızın projeleri yüklemesi veya MSBuild yüklenmesi gerekmeden işlem içi derlemeler yürütmesi gerektiğinde başvurun. Bu paket kullanılarak projelerin başarıyla değerlendirilmesi, bir uygulama dizinine ek bileşenler (derleyiciler gibi) toplama gerektirir. |
| [Microsoft. Build. Tasks. Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | MSBuild yaygın olarak kullanılan görevleri uygulayan Microsoft. Build. Tasks derlemesini içerir. |
| [Microsoft. Build. Utilities. Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | özel MSBuild görevleri uygulamak için kullanılan Microsoft. Build. Utilities derlemesini içerir. |

ayrıca NuGet, eski bir derlemeyi ( [Microsoft. Build. Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), kullanım dışı) barındırır.

MSBuild apı 'nin birkaç farklı sürümü vardır ve 15 ve 16 sürümleri için, NuGet paketlerindeki derlemelerin iki farklı biçimi vardır, biri .NET Framework ile derlenir ve .NET Framework apı yüzeyinin bir alt kümesi olan .net Core ile derlenir.  MSBuild .net Core sürümü, `dotnet` komutu çağırdığınızda ve Mac ve Linux sistemlerinde MSBuild kullanırken kullanılır.

MSBuild apı 'si belgeleri [.net apı tarayıcısı](/dotnet/api)kullanılarak veya aşağıdaki listedeki ad alanlarına göz atarak bulunabilir.

::: moniker range="vs-2017"
| Ad Alanı | Uygulanan Öğe | Açıklama |
|-----------| -----------| ----------- |
| [Microsoft. Build. Inşaat](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Tümü |  MSBuild nesne modelinin değerlendirilmeyecek değerlerle proje kökleri oluşturmak için kullandığı türleri içerir. Her proje kökü bir proje veya hedef dosyasına karşılık gelir. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Tümü | `ProjectOptions`Proje oluşturmayı destekleyen sınıfını içerir. |
| [Microsoft. Build. Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Tümü | MSBuild nesne modelinin projeleri değerlendirmek için kullandığı türleri içerir. Her proje bir veya daha fazla proje kökü ile ilişkilendirilir. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Tümü | `EvaluationContext`Çağrılar genelinde değerlendirme durumunu depolamak için kullanılan sınıfını içerir. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Tümü | Yapı işlemi sırasında oluşturulabilecek özel durum türlerini içerir. |
| [Microsoft.Build.Executıon](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Tümü | MSBuild nesne modelinin projeleri oluşturmak için kullandığı türleri içerir. |
| [Microsoft. Build. Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Tümü | görevlerin ve günlükçülerin MSBuild altyapısıyla nasıl etkileşime gireceğini tanımlayan türleri içerir.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Tümü | Performans profilini oluşturmayı destekleyen türleri içerir. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | yalnızca .NET Framework | Dosyalar, kurallar ve diğer kaynaklardan Ayrıştırılan XAML türlerini temsil etmek için kullanılan sınıfları içerir. |
| [Microsoft. Build. glob](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Tümü | Joker karakter işlemeyi destekleyen sınıflar içerir. |
| [Microsoft. Build. glob. Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Tümü | Joker karakter işlemeye yönelik uzantıları destekleyen türleri içerir. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Tümü | MSBuild anahtarını destekleyen türleri içerir `-graph` . |
| [Microsoft. Build. Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Tümü | Bir yapı ilerlemesini günlüğe kaydetmek için kullanılan türleri içerir. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Tümü | MSBuild 'da uzaktan iletişimi destekleyen türleri içerir. |
| [Microsoft. Build. Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Tümü | MSBuild tüm görevleri teslim etme uygulamasını içerir. |
| [Microsoft. Build. Tasks. Deployment. Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | yalnızca .NET Framework | MSBuild tarafından dahili olarak kullanılan sınıfları içerir. |
| [Microsoft. Build. Tasks. Deployment. bildirimli Estutilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | yalnızca .NET Framework | MSBuild tarafından kullanılan sınıfları içerir.|
| [Microsoft. Build. Tasks. Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Tümü | MSBuild tarafından dahili olarak kullanılan sınıfları içerir. |
| [Microsoft. Build. Tasks. xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | yalnızca .NET Framework | XAML derleme görevleriyle ilgili sınıfları içerir. |
| [Microsoft. Build. Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Tümü | kendi MSBuild günlükçüleri ve görevlerinizi oluşturmak için kullanabileceğiniz yardımcı sınıfları içerir.|
:::moniker-end
:::moniker range=">=vs-2019"
| Ad Alanı | Uygulanan Öğe | Açıklama |
|-----------| -----------| ----------- |
| [Microsoft. Build. Inşaat](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Tümü |  MSBuild nesne modelinin değerlendirilmeyecek değerlerle proje kökleri oluşturmak için kullandığı türleri içerir. Her proje kökü bir proje veya hedef dosyasına karşılık gelir. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Tümü | `ProjectOptions`Proje oluşturmayı destekleyen sınıfını içerir. |
| [Microsoft. Build. Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Tümü | MSBuild nesne modelinin projeleri değerlendirmek için kullandığı türleri içerir. Her proje bir veya daha fazla proje kökü ile ilişkilendirilir. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Tümü | `EvaluationContext`Çağrılar genelinde değerlendirme durumunu depolamak için kullanılan sınıfını içerir. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Tümü | Yapı işlemi sırasında oluşturulabilecek özel durum türlerini içerir. |
| [Microsoft.Build.Executıon](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Tümü | MSBuild nesne modelinin projeleri oluşturmak için kullandığı türleri içerir. |
| [Microsoft. Build. Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Tümü | görevlerin ve günlükçülerin MSBuild altyapısıyla nasıl etkileşime gireceğini tanımlayan türleri içerir.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Tümü | Performans profilini oluşturmayı destekleyen türleri içerir. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | yalnızca .NET Framework | Dosyalar, kurallar ve diğer kaynaklardan Ayrıştırılan XAML türlerini temsil etmek için kullanılan sınıfları içerir. |
| [Microsoft. Build. glob](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Tümü | Joker karakter işlemeyi destekleyen sınıflar içerir. |
| [Microsoft. Build. glob. Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Tümü | Joker karakter işlemeye yönelik uzantıları destekleyen türleri içerir. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Tümü | MSBuild anahtarını destekleyen türleri içerir `-graph` . |
| [Microsoft. Build. Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Tümü | Bir yapı ilerlemesini günlüğe kaydetmek için kullanılan türleri içerir. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Tümü | MSBuild 'da uzaktan iletişimi destekleyen türleri içerir. |
| [Microsoft. Build. Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Tümü | MSBuild tüm görevleri teslim etme uygulamasını içerir. |
| [Microsoft. Build. Tasks. Deployment. Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | yalnızca .NET Framework | MSBuild tarafından dahili olarak kullanılan sınıfları içerir. |
| [Microsoft. Build. Tasks. Deployment. bildirimli Estutilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | yalnızca .NET Framework | MSBuild tarafından kullanılan sınıfları içerir.|
| [Microsoft. Build. Tasks. Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Tümü | MSBuild tarafından dahili olarak kullanılan sınıfları içerir. |
| [Microsoft. Build. Tasks. xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | yalnızca .NET Framework | XAML derleme görevleriyle ilgili sınıfları içerir. |
| [Microsoft. Build. Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Tümü | kendi MSBuild günlükçüleri ve görevlerinizi oluşturmak için kullanabileceğiniz yardımcı sınıfları içerir.|
:::moniker-end

önceki tabloda, için geçerlidir sütunu, ad alanındaki türlerin hem .NET Framework hem de MSBuild apı 'sinin .net Core sürümlerinde kullanılabildiği anlamına gelir.
