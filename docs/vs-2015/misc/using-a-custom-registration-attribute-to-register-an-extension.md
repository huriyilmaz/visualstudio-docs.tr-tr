---
title: Bir uzantıyı kaydetmek için özel bir kayıt özniteliği kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935790"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Bir uzantıyı kaydetmek için özel bir kayıt özniteliği kullanma
Belirli durumlarda, uzantınızın yeni bir kayıt özniteliğini oluşturmanız gerekebilir. Kayıt özniteliklerini kullanarak yeni kayıt defteri anahtarları ekleyebilir veya varolan anahtarlara yeni değerler ekleyebilirsiniz. Yeni öznitelik öğesinden türetilmelidir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ve ve yöntemlerinin geçersiz kılması gerekir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-custom-attribute"></a>Özel öznitelik oluşturma  
 Aşağıdaki kod, yeni bir kayıt özniteliğinin nasıl oluşturulacağını gösterir.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 , Özniteliğin <xref:System.AttributeUsageAttribute> ilgili olduğu program öğesini (sınıf, yöntem, vb.) belirtmek için öznitelik sınıflarında kullanılır ve bir kereden fazla kullanılıp kullanılamayacağını ve devralınıp alınmayacağını belirtir.  
  
### <a name="creating-a-registry-key"></a>Kayıt defteri anahtarı oluşturma  
 Aşağıdaki kodda, özel öznitelik, kayıtlı olan VSPackage için anahtar altında **özel** bir alt anahtar oluşturur.  
  
```  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Mevcut bir kayıt defteri anahtarı altında yeni bir değer oluşturma  
 Varolan bir anahtara özel değerler ekleyebilirsiniz. Aşağıdaki kod, VSPackage kayıt anahtarına nasıl yeni bir değer ekleneceğini gösterir.  
  
```  
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