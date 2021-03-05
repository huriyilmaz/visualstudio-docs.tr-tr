---
description: Bu işlev, belirtilen projenin üst proje yolunu belirler.
title: SccGetParentProjectPath Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e624d8765da65dc6231c0128e87ffd9d6cdf848d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220618"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath işlevi
Bu işlev, belirtilen projenin üst proje yolunu belirler. Bu işlev, Kullanıcı kaynak denetimine bir Visual Studio projesi eklerken çağrılır.

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpUser

[in, out] Kullanıcı adı (en fazla SCC_USER_SIZE, NULL Sonlandırıcı dahil).

 lpProjPath

'ndaki Proje yolunu tanımlayan dize (NULL Sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpAuxProjPath

[in, out] Projeyi tanımlayan yardımcı dize (NULL Sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpParentProjPath

[in, out] Üst proje yolunu tanımlayan çıkış dizesi (NULL Sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Üst proje yolu başarıyla alındı.|
|SCC_E_INITIALIZEFAILED|Proje başlatılamadı.|
|SCC_E_INVALIDUSER|Kullanıcı, kaynak denetimi eklentisinde oturum açamadı.|
|SCC_E_UNKNOWNPROJECT|Proje, kaynak denetimi eklentisi tarafından bilinmiyor.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamayan dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje sözdizimi.|
|SCC_E_CONNECTIONFAILURE|Mağaza bağlantısı sorunu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev bir başarı veya hata kodu döndürür ve başarılı olursa, değişkeni `lpParentProjPath` belirtilen projenin tam proje yoluyla doldurur.

 Bu işlev, var olan bir projenin üst proje yolunu döndürür. Kök proje için işlev, geçirilen proje yolunu döndürür (yani, aynı kök proje yolu). Proje yolunun yalnızca kaynak denetimi eklentisi için anlamlı bir dize olduğunu unutmayın.

 IDE, `lpUser` ve parametrelerdeki değişiklikleri kabul etmek için hazır `lpAuxProjPath` . IDE bu dizeleri kalıcı hale getirin ve Kullanıcı bu projeyi gelecekte açtığında [SccOpenProject](../extensibility/sccopenproject-function.md) 'e iletir. Bu nedenle, bu dizeler, kaynak denetimi eklentisinin bir projeyle ilişkilendirilmesi gereken bilgileri izlemek için bir yol sağlar.

 Bu işlev, kullanıcıdan bir proje seçmesini istemez hariç, [SccGetProjPath](../extensibility/sccgetprojpath-function.md)öğesine benzerdir. Ayrıca hiçbir şekilde yeni bir proje oluşturmazlar ancak yalnızca var olan bir projeyle birlikte kullanılabilir.

 `SccGetParentProjectPath`Çağrıldığında `lpProjPath` ve `lpAuxProjPath` boş olmaz ve geçerli bir projeye karşılık gelir. Bu dizeler genellikle, işleve önceki bir çağrıdan IDE tarafından alınır `SccGetProjPath` .

 `lpUser`Bağımsız değişken kullanıcı adıdır. IDE, işlevinden daha önce aldığı Kullanıcı adına geçecek `SccGetProjPath` ve kaynak denetimi eklentisinin adı varsayılan olarak kullanması gerekir. Kullanıcının eklentiyle zaten açık bağlantısı varsa, eklentinin sessizce çalıştığından emin olmak için eklentinin herhangi bir istemi ortadan kaldırmaya çalışması gerekir. Ancak, oturum açma başarısız olursa, eklenti kullanıcıdan bir oturum açma isteği ister ve geçerli bir oturum açma bilgisi aldığında adı geri geçirin `lpUser` . Eklenti bu dizeyi değiştirebileceğinden, IDE her zaman bir arabellek boyutu ayırır ( `SCC_USER_LEN` + 1). Dize değiştirilirse, yeni dize geçerli bir oturum açma adı olmalıdır (en azından eski dize olarak geçerli olur).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Scccreatealt projesi ve SccGetParentProjectPath için teknik notlar
 Kaynak denetimine çözüm ve proje ekleme, bir kullanıcının kaynak denetim sisteminde konumları kaç kez seçmesi gerektiğini en aza indirmek için Visual Studio 'da basitleştirilmiştir. Bu değişiklikler, bir kaynak denetimi eklentisi yeni işlevlerin her ikisini de, [Scccreatealt projesi](../extensibility/scccreatesubproject-function.md) ve işlevini destekliyorsa, Visual Studio tarafından etkinleştirilir `SccGetParentProjectPath` . Ancak, aşağıdaki kayıt defteri girişi bu değişiklikleri devre dışı bırakmak ve önceki Visual Studio 'ya geri dönmek için kullanılabilir (kaynak denetimi eklentisi API sürüm 1,1) davranışı:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Bu kayıt defteri girdisi yoksa veya DWORD: 00000000 olarak ayarlandıysa, Visual Studio yeni işlevleri ve ' ı kullanmaya çalışır `SccCreateSubProject` `SccGetParentProjectPath` .

 Kayıt defteri girişi DWORD: 00000001 olarak ayarlandıysa, Visual Studio bu yeni işlevleri kullanmayı denemez ve kaynak denetimine ekleme işlemleri Visual Studio 'nun önceki sürümlerinde olduğu gibi çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
