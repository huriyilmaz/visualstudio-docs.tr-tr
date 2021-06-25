---
description: Bu işlev, belirtilen bir projenin üst proje yolunu belirler.
title: SccGetParentProjectPath İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a0a77808004c7bc8f408bbf34a3ed4f0715b36
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900141"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath işlevi
Bu işlev, belirtilen bir projenin üst proje yolunu belirler. Bu işlev, kullanıcı kaynak denetimine bir Visual Studio eklerken çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpUser

[in, out] Kullanıcı adı (NULL SCC_USER_SIZE kadar).

 lpProjPath

[in] Proje yolunu tanımlayan dize (NULL SCC_PRJPATH_SIZE kadar).

 lpUxProjPath

[in, out] Projeyi tanımlayan yardımcı dize (NULL SCC_PRJPATH_SIZE kadar).

 lpParentProjPath

[in, out] Üst proje yolunu tanımlayan çıkış dizesi (NULL SCC_PRJPATH_SIZE kadar).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Üst proje yolu başarıyla elde edildi.|
|SCC_E_INITIALIZEFAILED|Proje başlatılamadı.|
|SCC_E_INVALIDUSER|Kullanıcı kaynak denetimi eklentisinde oturum açamdı.|
|SCC_E_UNKNOWNPROJECT|Proje, kaynak denetimi eklentisi tarafından bilinmiyor.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamaz dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje söz dizimi.|
|SCC_E_CONNECTIONFAILURE|Depolama bağlantısı sorunu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev bir başarı veya hata kodu döndürür ve başarılı olursa değişkeni belirtilen projenin `lpParentProjPath` tam proje yolu ile doldurur.

 Bu işlev, mevcut projenin üst proje yolunu döndürür. Kök proje için işlev, geçirilen proje yolunu (yani aynı kök proje yolunu) döndürür. Proje yolunun yalnızca kaynak denetimi eklentisi için anlamlı bir dize olduğunu unutmayın.

 IDE, ve parametrelerinde yapılan değişiklikleri `lpUser` kabul `lpAuxProjPath` etmeye de hazırlanmıştır. Kullanıcı gelecekte bu projeyi açtığında IDE bu dizeleri kalıcı olarak [sccOpenProject'e](../extensibility/sccopenproject-function.md) iletir. Bu nedenle bu dizeler, kaynak denetim eklentisinin bir projeyle ilişkilendirmek için gereken bilgileri izlemesi için bir yol sağlar.

 Bu işlev [SccGetProjPath](../extensibility/sccgetprojpath-function.md)işlevine benzer, ancak kullanıcıdan bir proje seçmesini istemiz. Ayrıca hiçbir zaman yeni bir proje oluşturur, ancak yalnızca mevcut bir projeyle çalışır.

 çağrıldı `SccGetParentProjectPath` mı, `lpProjPath` boş olmaz ve geçerli bir projeye karşılık `lpAuxProjPath` gelecektir. Bu dizeler genellikle IDE tarafından işleve yapılan önceki bir çağrıdan `SccGetProjPath` alınmıştır.

 bağımsız `lpUser` değişkeni kullanıcı adıdır. IDE, işlevden daha önce aldığı kullanıcı adını iletir ve kaynak denetimi eklentisi varsayılan `SccGetProjPath` olarak bu adı kullanmalıdır. Kullanıcının eklentiyle açık bir bağlantısı varsa, işlevin sessizce çalışmasını sağlamak için eklenti tüm istemleri ortadan kaldırmayı denemeli. Ancak, oturum açma başarısız olursa, eklenti kullanıcıdan oturum açma isteminde olmalı ve geçerli bir oturum açma bilgileri aldığında adı 'ye geri `lpUser` iletir. Eklenti bu dizeyi değiştirene kadar, IDE her zaman boyutta bir arabellek ayırır ( `SCC_USER_LEN` +1). Dize değiştirilirse, yeni dize geçerli bir oturum açma adı (eski dize kadar geçerli) olmalıdır.

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject ve SccGetParentProjectPath için teknik notlar
 Kaynak denetimine çözüm ve proje ekleme işlemi Visual Studio kullanıcıdan kaynak denetim sisteminde konum seçmesi istendiğinde sayısını en aza indirmek için basitleştirildi. Bu değişiklikler, Visual Studio denetimi eklentisi hem yeni işlevleri hem [de SccCreateSubProject'i](../extensibility/scccreatesubproject-function.md) ve işlevi destekliyorsa bu değişiklikler Visual Studio tarafından `SccGetParentProjectPath` etkinleştirilir. Ancak, aşağıdaki kayıt defteri girdisi bu değişiklikleri devre dışı bırakmak ve önceki Visual Studio (Kaynak Denetimi Eklentisi API'si Sürüm 1.1) davranışına geri dönmek için kullanılabilir:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Bu kayıt defteri girdisi yoksa veya dword:00000000 olarak ayarlanırsa, Visual Studio ve işlevlerini kullanmayı `SccCreateSubProject` `SccGetParentProjectPath` denemez.

 Kayıt defteri girişi dword:00000001 olarak ayarlanırsa, Visual Studio bu yeni işlevleri kullanmaya çalışmaz ve kaynak denetimine ekleme işlemleri, önceki Visual Studio sürümlerinde olduğu gibi çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
