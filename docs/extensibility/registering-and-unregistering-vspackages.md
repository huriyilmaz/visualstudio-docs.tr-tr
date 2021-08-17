---
title: VSPackage'ları Kaydetme ve Kaydını | Microsoft Docs
description: Kullanabileceğiniz öznitelikler ve .pkgdef dosyası da dahil olmak üzere VSPackage'larınızı kaydetme ve kaydını çıkarma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 77929647b86f5397fa5986f2223b8e52c9d65c86
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041600"
---
# <a name="register-and-unregister-vspackages"></a>VSPackage'ları kaydetme ve kaydını çıkarma
VsPackage kaydetmek için öznitelikleri kullanır, ancak

## <a name="register-a-vspackage"></a>VSPackage kaydetme
 Yönetilen VSPackage'ların kaydını kontrol etmek için öznitelikleri kullanabilirsiniz. Tüm kayıt bilgileri bir *.pkgdef dosyasında* yer alan. Dosya tabanlı kayıt hakkında daha fazla bilgi için bkz. [CreatePkgDef yardımcı programı.](../extensibility/internals/createpkgdef-utility.md)

 Aşağıdaki kod, VSPackage'nızı kaydetmek için standart kayıt özniteliklerini nasıl kullanabileceğinizi gösterir.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Bir uzantının kaydını geri ala
 Birçok farklı VSPackage denemesi yaptıysanız ve bunları deneysel örnekten kaldırmak için Sıfırla  komutunu çalıştırabilirsiniz. Bilgisayarınızın **başlangıç Visual Studio Deneysel** Örneği sıfırla'yı bulun veya komut satırına şu komutu çalıştırın:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Visual Studio geliştirme örneğinize yüklemiş bir uzantıyı kaldırmak için Araçlar Uzantıları ve Güncelleştirmeler'e gidin, uzantıyı bulun ve  >  Kaldır'a **tıklayın.**

 Herhangi bir nedenle bu yöntemlerden hiçbiri uzantıyı kaldırmada başarılı olursa, VSPackage derlemesini komut satırına şu şekilde kaldırabilirsiniz:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Uzantıyı kaydetmek için özel kayıt özniteliği kullanma

Bazı durumlarda uzantınız için yeni bir kayıt özniteliği oluşturmanız gerekir. Yeni kayıt defteri anahtarları eklemek veya mevcut anahtarlara yeni değerler eklemek için kayıt özniteliklerini kullanabilirsiniz. Yeni öznitelik, 'den türetilen <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ve ve yöntemlerini geçersiz <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> kılması gerekir.

### <a name="create-a-custom-attribute"></a>Özel öznitelik oluşturma

Aşağıdaki kod, yeni bir kayıt özniteliğinin nasıl oluşturul olduğunu gösterir.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 özniteliği, özniteliğin ait olduğu program öğesini (sınıf, yöntem vb.), birden çok kez kullanılanın olup olmadığını ve devralınıp devralılamayacaklarını belirtmek için öznitelik <xref:System.AttributeUsageAttribute> sınıflarında kullanılır.

### <a name="create-a-registry-key"></a>Kayıt defteri anahtarı oluşturma

Aşağıdaki kodda, özel öznitelik, **kaydedilen** VSPackage anahtarının altında bir Özel alt anahtar oluşturur.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Mevcut kayıt defteri anahtarı altında yeni bir değer oluşturma

Mevcut bir anahtara özel değerler eklemek için kullanabilirsiniz. Aşağıdaki kod, VSPackage kayıt anahtarına yeni bir değer ekleme işlemini gösterir.

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
