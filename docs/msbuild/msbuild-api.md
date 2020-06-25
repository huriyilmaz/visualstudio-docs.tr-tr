---
title: MSBuild API 'SI | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e14f60e84611041294379108852f697c023cbcd8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350803"
---
# <a name="use-the-msbuild-api"></a>MSBuild API 'sini kullanma

MSBuild, programınızın derleme gerçekleştirebilmesi ve proje incelemesi yapabilmesi için ortak bir API yüzeyi sağlar. MSBuild API 'lerinin son sürümleri aşağıdaki NuGet paketlerinde bulunabilir:

| Paket adı | Description |
| ------------ | ----------- |
| [Microsoft. Build](https://www.nuget.org/packages/Microsoft.Build) | MSBuild projelerini oluşturmak, düzenlemek ve değerlendirmek için kullanılan Microsoft. Build derlemesini içerir.|
| [Microsoft. Build. Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Diğer MSBuild derlemeleri tarafından kullanılan ortak MSBuild çerçevesi derlemesini içerir. |
| [Microsoft. Build. Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | MSBuild 'in tamamen yürütülebilir bir kopyasını sunar. Bu pakete yalnızca uygulamanızın projeleri yüklemesi veya MSBuild 'in yüklenmesine gerek kalmadan işlem içi derlemeler yürütmesi gerektiğinde başvurun. Bu paket kullanılarak projelerin başarıyla değerlendirilmesi, bir uygulama dizinine ek bileşenler (derleyiciler gibi) toplama gerektirir. |
| [Microsoft. Build. Tasks. Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | MSBuild 'in yaygın olarak kullanılan görevlerini uygulayan Microsoft. Build. Tasks derlemesini içerir. |
| [Microsoft. Build. Utilities. Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Özel MSBuild görevlerini uygulamak için kullanılan Microsoft. Build. Utilities derlemesini içerir. |

Ayrıca, NuGet kullanım dışı olan [Microsoft. Build. Engine](https://www.nuget.org/packages/Microsoft.Build.Engine)eski bir derlemesini de barındırır.

MSBuild API 'nin birkaç farklı sürümü vardır ve 15 ve 16 sürümleri için, NuGet paketlerindeki derlemelerin iki ayrı biçimi vardır, .NET Framework bir tane ile derlenir ve .NET Framework API yüzeyinin bir alt kümesi olan .NET Core ile derlenir.  MSBuild 'in .NET Core sürümü `dotnet` , komutu çağırdığınızda ve Mac ve Linux sistemlerinde MSBuild kullanılırken kullanılır.

MSBuild API 'SI belgeleri [.NET API tarayıcısı](/dotnet/api)kullanılarak veya aşağıdaki listedeki ad alanlarına göz atarak bulunabilir.

| Ad Alanı | Uygulanan Öğe | Description |
|-----------| -----------| ----------- |
| [Microsoft. Build. Inşaat](/dotnet/api/Microsoft.Build.Construction) | Tümü |  MSBuild nesne modelinin değerlendirilmeyecek değerlerle proje kökleri oluşturmak için kullandığı türleri içerir. Her proje kökü bir proje veya hedef dosyasına karşılık gelir. |
| [Microsoft. Build. Definition](/dotnet/api/Microsoft.Build.Definition) | Tümü | `ProjectOptions`Proje oluşturmayı destekleyen sınıfını içerir. |
| [Microsoft. Build. Evaluation](/dotnet/api/Microsoft.Build.Evaluation) | Tümü | MSBuild nesne modelinin projeleri değerlendirmek için kullandığı türleri içerir. Her proje bir veya daha fazla proje kökü ile ilişkilendirilir. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context) | Tümü | `EvaluationContext`Çağrılar genelinde değerlendirme durumunu depolamak için kullanılan sınıfını içerir. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions) | Tümü | Yapı işlemi sırasında oluşturulabilecek özel durum türlerini içerir. |
| [Microsoft.Build.Executıon](/dotnet/api/Microsoft.Build.Execution) | Tümü | MSBuild nesne modelinin proje derlemek için kullandığı türleri içerir. |
| [Microsoft. Build. Framework](/dotnet/api/Microsoft.Build.Framework) | Tümü | Görevlerin ve günlükçülerin MSBuild altyapısıyla nasıl etkileşime gireceğini tanımlayan türleri içerir.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler) | Tümü | Performans profilini oluşturmayı destekleyen türleri içerir. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes) | Yalnızca .NET Framework | Dosyalar, kurallar ve diğer kaynaklardan Ayrıştırılan XAML türlerini temsil etmek için kullanılan sınıfları içerir. |
| [Microsoft. Build. glob](/dotnet/api/Microsoft.Build.Globbing) | Tümü | Joker karakter işlemeyi destekleyen sınıflar içerir. |
| [Microsoft. Build. glob. Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions) | Tümü | Joker karakter işlemeye yönelik uzantıları destekleyen türleri içerir. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph) | Tümü | MSBuild anahtarını destekleyen türleri içerir `-graph` . |
| [Microsoft. Build. Logging](/dotnet/api/Microsoft.Build.Logging) | Tümü | Bir yapı ilerlemesini günlüğe kaydetmek için kullanılan türleri içerir. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting) | Tümü | MSBuild 'de uzaktan iletişimi destekleyen türleri içerir. |
| [Microsoft. Build. Tasks](/dotnet/api/Microsoft.Build.Tasks) | Tümü | MSBuild ile tüm görevlerin dağıtımını içerir. |
| [Microsoft. Build. Tasks. Deployment. Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper) | Yalnızca .NET Framework | MSBuild tarafından dahili olarak kullanılan sınıfları içerir. |
| [Microsoft. Build. Tasks. Deployment. bildirimli Estutilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities) | Yalnızca .NET Framework | MSBuild 'in kullandığı sınıfları içerir.|
| [Microsoft. Build. Tasks. Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting) | Tümü | MSBuild tarafından dahili olarak kullanılan sınıfları içerir. |
| [Microsoft. Build. Tasks. xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml) | Yalnızca .NET Framework | XAML derleme görevleriyle ilgili sınıfları içerir. |
| [Microsoft. Build. Utilities](/dotnet/api/Microsoft.Build.Utilities) | Tümü | Kendi MSBuild Günlükçüleri ve görevlerinizi oluşturmak için kullanabileceğiniz yardımcı sınıfları içerir.|

Önceki tabloda, her biri Için geçerlidir sütununda, ad alanındaki türler MSBuild API 'sinin hem .NET Framework hem de .NET Core sürümlerinde kullanılabildiği anlamına gelir.
