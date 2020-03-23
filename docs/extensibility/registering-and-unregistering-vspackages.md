---
title: VSPackages'in Kaydedilmesi ve Kaydının Silinmesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303185"
---
# <a name="register-and-unregister-vspackages"></a>VSPackages'ı kaydetme ve kayıt dışı
Bir VSPackage'ı kaydetmek için öznitelikleri kullanırsınız, ancak

## <a name="register-a-vspackage"></a>VSPackage kaydedin
 Yönetilen VSPackages kaydını denetlemek için öznitelikleri kullanabilirsiniz. Tüm kayıt bilgileri *bir .pkgdef* dosyasında bulunur. Dosya tabanlı kayıt hakkında daha fazla bilgi için [CreatePkgDef yardımcı programı'na](../extensibility/internals/createpkgdef-utility.md)bakın.

 Aşağıdaki kod, VSPackage'ınızı kaydetmek için standart kayıt özniteliklerinin nasıl kullanılacağını gösterir.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Uzantını kayıt dışı
 Birçok farklı VSPackages ile deneme ler yapmaya başladıysanız ve bunları deneme örneğinden kaldırmak istiyorsanız, **sıfırlama** komutunu çalıştırabilirsiniz. Bilgisayarınızın başlangıç sayfasında **Visual Studio Deneme Örneğini Sıfırla'yı** arayın veya bu komutu komut satırından çalıştırın:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Visual Studio geliştirme örneğinize yüklediğiniz bir uzantıyı kaldırmak istiyorsanız, **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ne**gidin, uzantıyı bulun ve **Kaldır'ı**tıklatın.

 Bu yöntemlerden herhangi biri uzantıyı kaldırmayı başarırsa, KOMUT satırından VSPackage derlemesini aşağıdaki gibi çıkarabilirsiniz:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Uzantıyı kaydetmek için özel kayıt özniteliği kullanma

Bazı durumlarda uzantınız için yeni bir kayıt özniteliği oluşturmanız gerekebilir. Yeni kayıt defteri anahtarları eklemek veya varolan anahtarlara yeni değerler eklemek için kayıt özniteliklerini kullanabilirsiniz. Yeni öznitelik türemelisiniz <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, ve bu <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> ve <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> yöntemleri geçersiz kılmak gerekir.

### <a name="create-a-custom-attribute"></a>Özel bir öznitelik oluşturma

Aşağıdaki kod, yeni bir kayıt özniteliğinin nasıl oluşturultuğugösteriyi gösterir.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Öznitelik <xref:System.AttributeUsageAttribute> sınıflarında, özniteliğin ilgili olduğu program öğesini (sınıf, yöntem, vb.) belirtmek, birden fazla kez kullanılıp kullanılamayacağı ve devralınıp alınamayacağını belirtmek için kullanılır.

### <a name="create-a-registry-key"></a>Kayıt defteri anahtarı oluşturma

Aşağıdaki kodda, özel öznitelik, kayıtlı olan VSPackage için anahtarın altında **özel** bir alt anahtar oluşturur.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Varolan bir kayıt defteri anahtarı altında yeni bir değer oluşturma

Varolan bir anahtara özel değerler ekleyebilirsiniz. Aşağıdaki kod, VSPackage kayıt anahtarına nasıl yeni bir değer ekleyeceğinizi gösterir.

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
