---
title: VSPackages kaydetme ve kaydını silme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193824"
---
# <a name="registering-and-unregistering-vspackages"></a>VSPackage Kaydetme ve Kaydını Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öznitelikleri kullanarak VSPackage kaydedebilirsiniz, ancak  
  
## <a name="registering-a-vspackage"></a>VSPackage kaydetme  
 Yönetilen VSPackages kayıtlarını denetlemek için özniteliklerini kullanabilirsiniz. Tüm kayıt bilgileri bir. pkgdef dosyasında bulunur. Dosya tabanlı kayıt hakkında daha fazla bilgi için bkz. [CreatePkgDef Utility](../extensibility/internals/createpkgdef-utility.md).  
  
 Aşağıdaki kod, VSPackage 'ı kaydetmek için standart kayıt özniteliklerinin nasıl kullanılacağını gösterir.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Bir uzantının kaydını silme  
 Birçok farklı VSPackages ile denemeler yaptıysanız ve bunları deneysel örnekten kaldırmak istiyorsanız, yalnızca **Reset** komutunu çalıştırabilirsiniz. Bilgisayarınızın başlangıç sayfasındaki **Visual Studio Deneysel örneğini sıfırlayın** ' i veya komut satırından şu komutu çalıştırın:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Visual Studio 'nun geliştirme Örneğinizde yüklü olan bir uzantıyı kaldırmak istiyorsanız, **Araçlar/Uzantılar ve güncelleştirmeler**' e gidin, uzantıyı bulun ve **Kaldır**' ı tıklatın.  
  
 Bu yöntemlerin herhangi biri, uzantıyı kaldırmak için başarılı bir nedenden dolayı, VSPackage derlemesinin kaydını komut satırından aşağıdaki gibi silebilirsiniz:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)
