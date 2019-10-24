---
title: Bağlam parametreleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ea38b79be362f78fcc34161a480597fb0ecce40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727557"
---
# <a name="context-parameters"></a>Bağlam parametreleri
@No__t_0 tümleşik geliştirme ortamında (IDE), **Yeni proje**, **Yeni öğe Ekle**veya **alt proje** Ekle iletişim kutularına sihirbazları ekleyebilirsiniz. Eklenen sihirbazlar **Dosya** menüsünde veya **Çözüm Gezgini**bir projeye sağ tıklanarak kullanılabilir. IDE, sihirbazın uygulamasına bağlam parametrelerini geçirir. Bağlam parametreleri, IDE Sihirbazı çağırdığında projenin durumunu tanımlar.

 IDE, IDE 'deki <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> bayrağını proje için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> yöntemine ayarlayarak sihirbazları başlatır. Ayarlandığında proje, `IVsExtensibility::RunWizardFile` yönteminin, kayıtlı sihirbaz adı veya GUID 'SI ve IDE 'nin kendisine geçirdiği diğer bağlam parametreleri kullanılarak yürütülmesine neden olmalıdır.

## <a name="context-parameters-for-new-project"></a>Yeni proje için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıt Sihirbazı türü (<xref:EnvDTE.Constants.vsWizardNewProject>) veya sihirbazın türünü gösteren GUID. @No__t_0 uygulamasında, sihirbazın GUID 'SI {0F90E1D0-4999-11D1-B6D1-00A0C90F2744} olur. |
| `ProjectName` | Benzersiz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı olan bir dize. |
| `LocalDirectory` | Çalışma projesi dosyalarının yerel konumu. |
| `InstallationDirectory` | @No__t_0 dizin yolu yükleme. |
| `FExclusive` | Projenin açık çözümleri kapatması gerektiğini belirten Boolean bayrağı. |
| `SolutionName` | Çözüm dosyasının dizin bölümü veya *. sln* uzantısı olmadan adı. *. Suo* dosya adı, `SolutionName` kullanılarak da oluşturulur. Bu bağımsız değişken boş bir dize olmadığında, sihirbaz <xref:EnvDTE._Solution.AddFromTemplate%2A> bir projeyi eklemeden önce <xref:EnvDTE._Solution.Create%2A> kullanır. Bu ad boş bir dize ise, <xref:EnvDTE._Solution.Create%2A> çağrılmadan <xref:EnvDTE._Solution.AddFromTemplate%2A> kullanın. |
| `Silent` | Sihirbazın, **son** tıklandığı gibi sessizce çalıştırılıp çalıştırılmayacağını belirten Boole değeri (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Yeni öğe Ekle için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıt Sihirbazı türü (<xref:EnvDTE.Constants.vsWizardAddItem>) veya sihirbazın türünü gösteren GUID. @No__t_0 uygulamasında, sihirbazın GUID 'SI {0F90E1D1-4999-11D1-B6D1-00A0C90F2744} olur. |
| `ProjectName` | Benzersiz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı olan bir dize. |
| `ProjectItems` | Çalışma projesi dosyalarını içeren yerel konum. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, kullanıcının **öğe Ekle** iletişim kutusundan aldığı varsayılan dosya adı veya dosya adıdır. Ad, *. vsdir* dosyasında ayarlanan bayrakları temel alır. Ad, null bir değer olabilir. |
| `InstallationDirectory` | @No__t_0 dizin yolu yükleme. |
| `Silent` | Sihirbazın, **son** tıklandığı gibi sessizce çalıştırılıp çalıştırılmayacağını belirten Boole değeri (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Alt proje Ekle için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıt Sihirbazı türü (<xref:EnvDTE.Constants.vsWizardAddSubProject>) veya sihirbazın türünü gösteren GUID. @No__t_0 uygulamasında, sihirbazın GUID 'SI {0F90E1D2-4999-11D1-B6D1-00A0C90F2744} olur. |
| `ProjectName` | Benzersiz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı olan bir dize. |
| `ProjectItems` | Sihirbazın üzerinde çalıştığı `ProjectItems` koleksiyonuna yönelik işaretçi. Bu işaretçi, proje hiyerarşisi seçimine göre sihirbaza geçirilir. Kullanıcı genellikle öğenin ekleneceği bir klasörü seçer ve ardından projenin **öğe Ekle** iletişim kutusunu çağırır. |
| `LocalDirectory` | Çalışma projesi dosyalarının yerel konumu. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, kullanıcının **öğe Ekle** iletişim kutusundan aldığı varsayılan dosya adı veya dosya adıdır. Ad, *. vsdir* dosyasında ayarlanan bayrakları temel alır. Ad, null bir değer olabilir. |
| `InstallationDirectory` | @No__t_0 yüklemesinin dizin yolu. |
| `Silent` | Sihirbazın, **son** tıklandığı gibi sessizce çalıştırılıp çalıştırılmayacağını belirten Boole değeri (`TRUE`). |

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Özel parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (. vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Sihirbazları başlatmak için bağlam parametreleri](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)