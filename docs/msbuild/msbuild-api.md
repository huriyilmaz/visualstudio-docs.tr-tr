---
title: MSBuild API | Microsoft Docs
description: Program'ın derlemeler gerçekleştirerek MSBuild inceleyemesi için sağladığı genel API yüzeyi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 54b1f78dacdc0d1bf18d722f00e2d1bfd665094e6ef154868cc54890cde313a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427658"
---
# <a name="use-the-msbuild-api"></a>MSBuild API'sini kullanma

MSBuild programınız derlemeler gerçekleştirerek projeleri inceleyemesi için genel bir API yüzeyi sağlar. MSBuild API'lerinin son sürümleri aşağıdaki NuGet bulunabilir:

| Paket adı | Açıklama |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | Proje oluşturmak, düzenlemek ve değerlendirmek için kullanılan Microsoft.Build derlemesini MSBuild içerir.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Diğer derlemeler tarafından MSBuild ortak çerçeve derlemesini MSBuild içerir. |
| [Microsoft.Build.Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Dosyanın tam bir yürütülebilir MSBuild. Bu pakete yalnızca, uygulamanın proje yüklemesi veya işlem sırasında derlemeleri, uygulama yüklemesi gerekmeden yürütmesi MSBuild. Projelerin bu paketi kullanarak başarıyla değerlendirilmesi için bir uygulama dizininde ek bileşenlerin (derleyiciler gibi) toplaması gerekir. |
| [Microsoft.Build.Tasks.Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Uygulamanın yaygın olarak kullanılan görevlerini uygulayan Microsoft.Build.Tasks derleme MSBuild. |
| [Microsoft.Build.Utilities.Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Özel dağıtım görevleri uygulamak için kullanılan Microsoft.Build.Utilities derleme MSBuild içerir. |

Ayrıca, NuGet, kullanım dışı olan eski bir derleme olan [Microsoft.Build.Engine'i](https://www.nuget.org/packages/Microsoft.Build.Engine)de barındırr.

MSBuild API'nin birkaç farklı sürümü vardır ve 15 ve 16 sürümleri için, derlemelerin NuGet paketlerinde biri .NET Framework ile derlenmiş ve diğeri de .NET Framework API yüzeyinin bir alt kümesi olan .NET Core ile derlenmiş iki farklı derleme formu vardır.  MSBuild.NET Core sürümü, komutu çağırarak Mac ve `dotnet` Linux MSBuild.NET Core sürümü kullanılır.

MSBuild API'si [belgeleri.NET API Tarayıcısı](/dotnet/api)kullanılarak veya aşağıdaki listede ad alanlarına göz atarak bulunabilir.

::: moniker range="vs-2017"
| Ad Alanı | Uygulanan Öğe | Açıklama |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Tümü |  Örnek nesne modelinin MSBuild değerlerle proje kökleri oluşturmak için kullandığı türleri içerir. Her proje kökü bir projeye veya hedef dosyasına karşılık gelen bir dosyadır. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Tümü | Proje `ProjectOptions` projesini destekleyen sınıfını içerir. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Tümü | Nesne modelinin projeleri değerlendirmek MSBuild için kullandığı türleri içerir. Her proje bir veya daha fazla proje kökleriyle ilişkilendirildi. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Tümü | Değerlendirme durumunu `EvaluationContext` çağrılar arasında depolamak için kullanılan sınıfını içerir. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Tümü | Derleme işlemi sırasında atılan özel durum türlerini içerir. |
| [Microsoft.Build.Exekesme](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Tümü | Nesne modelinin MSBuild için kullandığı türleri içerir. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Tümü | Görevlerin ve günlük kullanıcılarının MSBuild içerir.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Tümü | Performans profili oluşturmayı destekleyen türleri içerir. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | .NET Framework yalnızca | Dosyalardan, kurallardan ve diğer kaynaklardan ayrıştıran XAML türlerini temsil etmek için kullanılan sınıfları içerir. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Tümü | Joker karakter işlemeyi destekleyen sınıflar içerir. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Tümü | Joker karakter işleme uzantılarını destekleyen türleri içerir. |
| [Microsoft.Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Tümü | Anahtar anahtarını destekleyen `-graph` MSBuild içerir. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Tümü | Derlemenin ilerlemesini günlüğe kaydetme için kullanılan türleri içerir. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Tümü | Verilerdemoteyi destekleyen türleri MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Tümü | Verilerle birlikte gönderim yapılan tüm görevlerin MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | .NET Framework yalnızca | Uygulama tarafından dahili olarak kullanılan sınıfları MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | .NET Framework yalnızca | Uygulama tarafından MSBuild içerir.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Tümü | Uygulama tarafından dahili olarak kullanılan sınıfları MSBuild. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | .NET Framework yalnızca | XAML derleme görevleriyle ilgili sınıfları içerir. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Tümü | Kendi günlüklerinizi ve görevlerinizi oluşturmak için kullanabileceğiniz MSBuild sınıflarını içerir.|
:::moniker-end
:::moniker range=">=vs-2019"
| Ad Alanı | Uygulanan Öğe | Açıklama |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Tümü |  Örnek nesne modelinin MSBuild değerlerle proje kökleri oluşturmak için kullandığı türleri içerir. Her proje kökü bir projeye veya hedef dosyasına karşılık gelen bir dosyadır. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Tümü | Proje `ProjectOptions` projesini destekleyen sınıfını içerir. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Tümü | Nesne modelinin projeleri değerlendirmek MSBuild için kullandığı türleri içerir. Her proje bir veya daha fazla proje kökleriyle ilişkilendirildi. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Tümü | Değerlendirme durumunu `EvaluationContext` çağrılar arasında depolamak için kullanılan sınıfını içerir. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Tümü | Derleme işlemi sırasında atılan özel durum türlerini içerir. |
| [Microsoft.Build.Exekesme](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Tümü | Nesne modelinin MSBuild için kullandığı türleri içerir. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Tümü | Görevlerin ve günlük kullanıcılarının veri altyapısıyla nasıl etkileşime MSBuild içerir.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Tümü | Performans profili oluşturmayı destekleyen türleri içerir. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | .NET Framework yalnızca | Dosyalardan, kurallardan ve diğer kaynaklardan ayrıştıran XAML türlerini temsil etmek için kullanılan sınıfları içerir. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Tümü | Joker karakter işlemeyi destekleyen sınıflar içerir. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Tümü | Joker karakter işleme uzantılarını destekleyen türleri içerir. |
| [Microsoft.Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Tümü | Anahtar anahtarını destekleyen `-graph` MSBuild içerir. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Tümü | Derlemenin ilerlemesini günlüğe kaydetme için kullanılan türleri içerir. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Tümü | Verilerdemoteyi destekleyen türleri MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Tümü | Verilerle birlikte gönderim yapılan tüm görevlerin MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | .NET Framework yalnızca | Uygulama tarafından dahili olarak kullanılan sınıfları MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | .NET Framework yalnızca | Uygulama tarafından MSBuild içerir.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Tümü | Uygulama tarafından dahili olarak kullanılan sınıfları MSBuild. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | .NET Framework yalnızca | XAML derleme görevleriyle ilgili sınıfları içerir. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Tümü | Kendi günlüklerinizi ve görevlerinizi oluşturmak için kullanabileceğiniz MSBuild sınıflarını içerir.|
:::moniker-end

Önceki tabloda, Uygulandığı Sütundaki All, ad alanı türlerinin .NET Framework API'sinde ve MSBuild API'sinde kullanılabilir olduğu anlamına gelir.
