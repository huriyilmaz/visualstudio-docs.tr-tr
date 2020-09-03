---
title: VSPackages kaydetme ve kaydını silme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f345bdbd3cf5858d495937c743b580abf5e3dd50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701589"
---
# <a name="register-and-unregister-vspackages"></a>VSPackages kaydetme ve kaydını silme
Öznitelikleri kullanarak VSPackage kaydedebilirsiniz, ancak

## <a name="register-a-vspackage"></a>VSPackage kaydetme
 Yönetilen VSPackages kayıtlarını denetlemek için özniteliklerini kullanabilirsiniz. Tüm kayıt bilgileri bir *. pkgdef* dosyasında bulunur. Dosya tabanlı kayıt hakkında daha fazla bilgi için bkz. [CreatePkgDef Utility](../extensibility/internals/createpkgdef-utility.md).

 Aşağıdaki kod, VSPackage 'ı kaydetmek için standart kayıt özniteliklerinin nasıl kullanılacağını gösterir.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Bir uzantının kaydını silme
 Birçok farklı VSPackages ile denemeler yaptıysanız ve bunları deneysel örnekten kaldırmak istiyorsanız, yalnızca **Reset** komutunu çalıştırabilirsiniz. Bilgisayarınızın başlangıç sayfasındaki **Visual Studio Deneysel örneğini sıfırlayın** ' i veya komut satırından şu komutu çalıştırın:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Visual Studio 'nun geliştirme örneğinize yüklediğiniz bir uzantıyı kaldırmak istiyorsanız, **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' e gidin, uzantıyı bulun ve **Kaldır**' a tıklayın.

 Bu yöntemlerin herhangi biri, uzantıyı kaldırmak için başarılı bir nedenden dolayı, VSPackage derlemesinin kaydını komut satırından aşağıdaki gibi silebilirsiniz:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Bir uzantıyı kaydetmek için özel bir kayıt özniteliği kullanma

Belirli durumlarda, uzantınızın yeni bir kayıt özniteliğini oluşturmanız gerekebilir. Kayıt özniteliklerini kullanarak yeni kayıt defteri anahtarları ekleyebilir veya varolan anahtarlara yeni değerler ekleyebilirsiniz. Yeni öznitelik öğesinden türetilmelidir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ve ve yöntemlerinin geçersiz kılması gerekir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .

### <a name="create-a-custom-attribute"></a>Özel öznitelik oluştur

Aşağıdaki kod, yeni bir kayıt özniteliğinin nasıl oluşturulacağını gösterir.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 , Özniteliğin <xref:System.AttributeUsageAttribute> ilgili olduğu program öğesini (sınıf, yöntem, vb.) belirtmek için öznitelik sınıflarında kullanılır ve bir kereden fazla kullanılıp kullanılamayacağını ve devralınıp alınmayacağını belirtir.

### <a name="create-a-registry-key"></a>Kayıt defteri anahtarı oluşturma

Aşağıdaki kodda, özel öznitelik, kayıtlı olan VSPackage için anahtar altında **özel** bir alt anahtar oluşturur.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Mevcut bir kayıt defteri anahtarı altında yeni bir değer oluştur

Varolan bir anahtara özel değerler ekleyebilirsiniz. Aşağıdaki kod, VSPackage kayıt anahtarına nasıl yeni bir değer ekleneceğini gösterir.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../extensibility/internals/vspackages.md)
