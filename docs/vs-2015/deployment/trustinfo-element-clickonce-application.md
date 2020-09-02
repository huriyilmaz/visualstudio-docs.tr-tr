---
title: '&lt;TrustInfo &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca7e19925288b1509fec08235f546b84b4afffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62420083"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;TrustInfo &gt; öğesi (ClickOnce uygulaması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanın istemci bilgisayarda çalışması için gereken en düşük güvenlik izinlerini açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <trustInfo>  
   <security>  
      <applicationRequestMinimum>  
         <PermissionSet  
            ID  
            Unrestricted>  
            <IPermission  
               class  
               version  
               Unrestricted  
            />  
         </PermissionSet>  
         <defaultAssemblyRequest  
            permissionSetReference  
         />  
         <assemblyRequest  
            name  
            permissionSetReference  
         />  
      </applicationRequestMinimum>  
      <requestedPrivileges>  
         <requestedExecutionLevel  
            level  
            uiAccess  
         />  
      </requestedPrivileges>  
   </security>  
</trustInfo>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `trustInfo`Öğesi gereklidir ve `asm.v2` ad alanında bulunur. Öznitelikleri yoktur ve aşağıdaki öğeleri içerir.  
  
## <a name="security"></a>güvenlik  
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `trustInfo` . `applicationRequestMinimum`Öğesi içerir ve özniteliği yoktur.  
  
## <a name="applicationrequestminimum"></a>applicationRequestMinimum  
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `security` ve `PermissionSet` ,, `assemblyRequest` ve öğelerini içerir `defaultAssemblyRequest` . Bu öğenin öznitelikleri yok.  
  
## <a name="permissionset"></a>PermissionSet  
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `applicationRequestMinimum` ve `IPermission` öğesi içerir. Bu öğe aşağıdaki özniteliklere sahiptir.  
  
- `ID`  
  
     Gereklidir. İzin kümesini tanımlar. Bu öznitelik herhangi bir değer olabilir. KIMLIĞE `defaultAssemblyRequest` ve özniteliklerine göre başvurulur `assemblyRequest` .  
  
- `version`  
  
     Gereklidir. İznin sürümünü tanımlar. Normalde bu değer `1` .  
  
## <a name="ipermission"></a>IPermission  
 İsteğe bağlı. Bu öğe, öğesinin bir alt öğesidir `PermissionSet` . `IPermission`Öğesi içindeki bir izin sınıfını tam olarak tanımlar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . `IPermission`Öğesi aşağıdaki özniteliklere sahiptir, ancak izin sınıfındaki özelliklere karşılık gelen ek özniteliklere sahip olabilir. Belirli bir iznin sözdizimini öğrenmek için Security.config dosyasında listelenen örneklere bakın.  
  
- `class`  
  
     Gereklidir. İzin sınıfını tanımlayıcı ada göre tanımlar. Örneğin, aşağıdaki kod `FileDialogPermission` türü tanımlar.  
  
     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
- `version`  
  
     Gereklidir. İznin sürümünü tanımlar. Genellikle bu değer `1` .  
  
- `Unrestricted`  
  
     Gereklidir. Uygulamanın bu iznin Kısıtlanmamış izni olup olmadığını belirler. Varsa `true` , izin verme koşulsuz olur. Eğer `false` veya bu öznitelik tanımlanmamışsa, etiketinde tanımlanan izne özgü özniteliklere göre kısıtlanır `IPermission` . Aşağıdaki izinleri alın:  
  
    ```  
    <IPermission  
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Read="USERNAME" />  
    <IPermission  
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Unrestricted="true" />  
    ```  
  
     Bu örnekte, için bildirimi, <xref:System.Security.Permissions.EnvironmentPermission> uygulamayı yalnızca ortam değişkeni Kullanıcı adı ' nı okumak üzere kısıtlar, ancak bildirimi, <xref:System.Security.Permissions.FileDialogPermission> uygulamanın tüm sınıfların sınırsız kullanımını sağlar <xref:System.Windows.Forms.FileDialog> .  
  
## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest  
 İsteğe bağlı. Tüm derlemelere verilen izin kümesini tanımlar. Bu öğe, öğesinin bir alt öğesidir `applicationRequestMinimum` ve aşağıdaki özniteliğe sahiptir.  
  
- `permissionSetReference`  
  
     Gereklidir. Varsayılan izin olan izin kümesinin KIMLIĞINI tanımlar. İzin kümesi, `PermissionSet` öğesinde bildirilmiştir.  
  
## <a name="assemblyrequest"></a>assemblyRequest  
 İsteğe bağlı. Belirli bir derleme için izinleri tanımlar. Bu öğe, öğesinin bir alt öğesidir `applicationRequestMinimum` ve aşağıdaki özniteliklere sahiptir.  
  
- `Name`  
  
     Gereklidir. Derleme adını tanımlar.  
  
- `permissionSetReference`  
  
     Gereklidir. Bu derlemenin gerektirdiği izin kümesinin KIMLIĞINI tanımlar. İzin kümesi, `PermissionSet` öğesinde bildirilmiştir.  
  
## <a name="requestedprivileges"></a>requestedPrivileges  
 İsteğe bağlı. Bu öğe, öğesinin bir alt öğesidir `security` ve `requestedExecutionLevel` öğesi içerir. Bu öğenin öznitelikleri yok.  
  
## <a name="requestedexecutionlevel"></a>requestedExecutionLevel  
 İsteğe bağlı. Uygulama isteklerinin çalıştırılacağı güvenlik düzeyini tanımlar. Bu öğenin alt öğesi yoktur ve aşağıdaki özniteliklere sahiptir.  
  
- `Level`  
  
     Gereklidir. Uygulamanın istediği güvenlik düzeyini gösterir. Olası değerler şunlardır:  
  
     `asInvoker`, ek izin isteme. Bu düzey hiçbir ek güven istemi gerektirmez.  
  
     `highestAvailable`, üst işlem için kullanılabilir en yüksek izinleri istiyor.  
  
     `requireAdministrator`, tam yönetici izinleri istiyor.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar yalnızca değeri ile yüklenir `asInvoker` . Başka bir değerle yükleme başarısız olur.  
  
- `uiAccess`  
  
     İsteğe bağlı. Uygulamanın korumalı Kullanıcı Arabirimi öğelerine erişim gerektirip gerektirmediğini belirtir. Değerler ya da `true` `false` şeklindedir ve varsayılan değer false 'dur. Yalnızca imzalı uygulamalar true değerine sahip olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama, istemci bilgisayardan varsayılan olarak izin vereceğinden daha fazla izin isterse, ortak dil çalışma zamanının güven Yöneticisi, uygulamaya Bu yükseltilmiş güven düzeyini vermek isterse kullanıcıyı sorar. Hayır yazmazsa uygulama çalışmaz; Aksi takdirde, istenen izinlerle çalıştırılır.  
  
 Ve kullanılarak istenen tüm `defaultAssemblyRequest` İzinler `assemblyRequest` , dağıtım bildiriminin geçerli bir güven lisansına sahip olup olmadığını Kullanıcı istenmeden alacak şekilde verilecek.  
  
 Izin yükseltme hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md). İlke dağıtımı hakkında daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki üç kod örneği, `trustInfo` bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımın uygulama bildiriminde kullanılmak üzere varsayılan adlandırılmış güvenlik bölgelerinin (Internet, LocalIntranet ve FullTrust) öğelerini gösterir.  
  
 İlk örnek, `trustInfo` Internet güvenlik bölgesinde bulunan varsayılan izinler için öğesini gösterir.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="Internet">  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Access="Open" />  
          <IPermission  
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"  
            Allowed="DomainIsolationByUser"  
            UserQuota="10240" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Flags="Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Window="SafeTopLevelWindows"  
            Clipboard="OwnClipboard" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"   
            Level="SafePrinting" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="Internet" />  
      </applicationRequestMinimum>  
    </security>  
  </trustInfo>  
```  
  
 İkinci örnek, `trustInfo` LocalIntranet güvenlik bölgesinde bulunan varsayılan izinler için öğesini gösterir.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="LocalIntranet">  
          <IPermission  
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Read="USERNAME" />  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Allowed="AssemblyIsolationByUser"  
            UserQuota="9223372036854775807"  
            Expiry="9223372036854775807"  
            Permanent="True" />  
          <IPermission  
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="ReflectionEmit" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="Assertion, Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"  
            Level="DefaultPrinting" />  
          <IPermission  
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />  
      </applicationRequestMinimum>  
    </security>  
</trustInfo>  
```  
  
 Üçüncü örnek, `trustInfo` FullTrust güvenlik bölgesinde bulunan varsayılan izinler için öğesini gösterir.  
  
```  
<trustInfo>  
  <security>  
    <applicationRequestMinimum>  
      <PermissionSet ID="FullTrust" Unrestricted="true" />  
      <defaultAssemblyRequest permissionSetReference="FullTrust" />  
    </applicationRequestMinimum>  
  </security>  
</trustInfo>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
