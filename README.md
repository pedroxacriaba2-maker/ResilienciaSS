// RESILIÊNCIA SS - LOADER

const RESILIENCIA_SS = "https://raw.githubusercontent.com/SEUUSUARIO/ResilienciaSS/main/ResilienciaSS.js"

let req = new Request(RESILIENCIA_SS)
let code = await req.loadString()

if (!code || code.startsWith("404")) {
  let a = new Alert()
  a.title = "RESILIÊNCIA SS"
  a.message = "❌ Não foi possível baixar o script do GitHub.\nVerifique o link ou conexão."
  a.addAction("OK")
  await a.present()
} else {
  try {
    eval(code)
  } catch (e) {
    let a = new Alert()
    a.title = "RESILIÊNCIA SS"
    a.message = "⚠️ Erro ao executar o script:\n\n" + e
    a.addAction("OK")
    await a.present()
  }
}
