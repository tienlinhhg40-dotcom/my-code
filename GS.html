/*************************************************
 * 🎓 APP HỌC TẬP CHO BÉ - FULL FINAL ULTIMATE PRO
 * - Học tập / Kiểm tra
 * - Kho quà
 * - Thú cưng
 * - Đấu trường PK
 * - Phụ huynh chỉnh sao
 * - Nâng cấp pet shop / reward / pet care
 *************************************************/

function onOpen() {
  SpreadsheetApp.getUi()
    .createMenu("🎓 APP HỌC TẬP")
    .addItem("▶️ Mở App", "showApp")
    .addToUi();
}

function showApp() {
  const html = HtmlService.createHtmlOutputFromFile("Index")
    .setTitle("🎓 App Học Tập Cho Bé")
    .setWidth(1600)
    .setHeight(950);
  SpreadsheetApp.getUi().showModalDialog(html, "🎓 App Học Tập Cho Bé");
}

/*************************************************
 * 📌 CONFIG SHEET
 *************************************************/
const SHEET_HOCSINH = "HocSinh";
const SHEET_TOAN = "Toan";
const SHEET_TV = "TiengViet";
const SHEET_ANH = "TiengAnh";
const SHEET_KETQUA = "KetQua";
const SHEET_PETS = "Pets";
const SHEET_PARENT_LOG = "ParentLog";

function getSS() {
  return SpreadsheetApp.getActiveSpreadsheet();
}

function getSheet(name) {
  return getSS().getSheetByName(name);
}

function ensureSheet(name, headers) {
  let sh = getSheet(name);
  if (!sh) {
    sh = getSS().insertSheet(name);
    if (headers && headers.length) {
      sh.getRange(1, 1, 1, headers.length).setValues([headers]);
    }
  }
  return sh;
}

/*************************************************
 * 🚀 INIT DATA
 *************************************************/
function getInitialData() {
  ensureAllSheets();

  return {
    hocSinh: getHocSinhData(),
    topicsToan: getTopicsFromSheet(SHEET_TOAN),
    topicsTV: getTopicsFromSheet(SHEET_TV),
    topicsAnh: getTopicsFromSheet(SHEET_ANH),
    pets: getAllPetCatalog()
  };
}

function ensureAllSheets() {
  ensureSheet(SHEET_HOCSINH, [
    "Tên Bé", "Tuổi", "Sao", "Quà", "PetsJson", "BattleWin", "BattleLose"
  ]);

  ensureSheet(SHEET_TOAN, [
    "Câu hỏi", "Đáp án đúng", "Độ tuổi", "Chủ đề", "Hình ảnh"
  ]);

  ensureSheet(SHEET_TV, [
    "Câu hỏi", "Đáp án đúng", "Độ tuổi", "Chủ đề", "Hình ảnh"
  ]);

  ensureSheet(SHEET_ANH, [
    "Câu hỏi", "Đáp án đúng", "Độ tuổi", "Chủ đề", "Hình ảnh"
  ]);

  ensureSheet(SHEET_KETQUA, [
    "Thời gian", "Tên Bé", "Tuổi", "Môn", "Chế độ", "Câu hỏi", "Đáp án đúng", "Trả lời", "Kết quả", "Sao nhận"
  ]);

  ensureSheet(SHEET_PETS, [
    "ID", "Tên", "Emoji", "Giá", "Độ hiếm", "ATK", "HP", "Skill", "SkillType"
  ]);

  ensureSheet(SHEET_PARENT_LOG, [
    "Thời gian", "Tên Bé", "Điều chỉnh sao", "Ghi chú", "Sao sau chỉnh"
  ]);

  seedDefaultDataIfNeeded();
}

function seedDefaultDataIfNeeded() {
  const petSheet = getSheet(SHEET_PETS);
  if (petSheet.getLastRow() <= 1) {
    const pets = [
      ["pet_001","Mèo Lửa","🐱",0,"Thường",12,100,"Cào Lửa","fire"],
      ["pet_002","Cún Băng","🐶",50,"Thường",13,105,"Băng Giá","ice"],
      ["pet_003","Thỏ Sét","🐰",100,"Hiếm",16,98,"Tia Chớp","laser"],
      ["pet_004","Gấu Trống","🐻",200,"Hiếm",18,115,"Gầm Sóng Âm","sound"],
      ["pet_005","Cáo Đất","🦊",300,"Siêu hiếm",20,120,"Địa Chấn","earth"],
      ["pet_006","Rồng Nước","🐉",400,"Siêu hiếm",23,135,"Thuỷ Long","water"],
      ["pet_007","Kỳ Lân","🦄",500,"Huyền thoại",28,150,"Cầu Vồng","rainbow"],
      ["pet_008","Bạch Tuộc Mực","🐙",1000,"Siêu hiếm",19,125,"Mực Đen","ink"],
      ["pet_009","Phượng Hoàng","🦅",2000,"Huyền thoại",30,160,"Lửa Tái Sinh","phoenix"],
      ["pet_010","Rắn Độc","🐍",300,"Siêu hiếm",24,118,"Nọc Độc","poison"],
      ["pet_011","Hổ Tốc Độ","🐯",500,"Huyền thoại",27,140,"Trảo Nhanh","speed"],
      ["pet_012","Cá Mập Kiếm","🦈",400,"Siêu hiếm",25,130,"Chém Biển","slash"],
      ["pet_013","Công Pha Lê","🦚",1000,"Huyền thoại",31,170,"Lông Pha Lê","magic"],
      ["pet_014","Rồng Bóng Đêm","🐲",2000,"Huyền thoại",35,185,"Bóng Đêm","magic"],
      ["pet_015","Sư Tử Vàng","🦁",5000,"Thần thoại",42,220,"Gầm Hoàng Kim","fire"],
      ["pet_016","Cá Heo Ánh Sáng","🐬",300,"Hiếm",18,122,"Sóng Sáng","water"],
      ["pet_017","Bướm Tiên","🦋",200,"Hiếm",15,95,"Bụi Phép","magic"],
      ["pet_018","Sói Tuyết","🐺",1000,"Huyền thoại",32,175,"Băng Nanh","ice"],
      ["pet_019","Rùa Kim Cương","🐢",500,"Siêu hiếm",20,210,"Mai Cứng","earth"],
      ["pet_020","Chim Sấm","🦜",400,"Siêu hiếm",22,128,"Sét Gió","laser"]
    ];
    petSheet.getRange(2,1,pets.length,pets[0].length).setValues(pets);
  }

  const hsSheet = getSheet(SHEET_HOCSINH);
  if (hsSheet.getLastRow() <= 1) {
    const defaultPets = JSON.stringify([
      {
        id: "pet_001",
        level: 1,
        exp: 0,
        evolution: 1,
        fashion: "Mặc định",
        ownedAt: new Date().toISOString()
      }
    ]);

    hsSheet.getRange(2,1,2,7).setValues([
      ["Bé Na", 6, 50, "", defaultPets, 0, 0],
      ["Bé Bo", 7, 50, "", defaultPets, 0, 0]
    ]);
  }
}

/*************************************************
 * 👦 HỌC SINH
 *************************************************/
function getHocSinhData() {
  const sh = getSheet(SHEET_HOCSINH);
  const values = sh.getDataRange().getValues();
  if (values.length <= 1) return [];

  return values.slice(1).filter(r => r[0]).map(r => ({
    ten: r[0],
    tuoi: r[1],
    sao: Number(r[2] || 0),
    qua: r[3] || "",
    petsJson: r[4] || "",
    battleWin: Number(r[5] || 0),
    battleLose: Number(r[6] || 0)
  }));
}

function findStudentRow(tenBe) {
  const sh = getSheet(SHEET_HOCSINH);
  const data = sh.getDataRange().getValues();
  for (let i = 1; i < data.length; i++) {
    if (String(data[i][0]).trim() === String(tenBe).trim()) return i + 1;
  }
  return -1;
}

function getStudentByName(tenBe) {
  return getHocSinhData().find(x => x.ten === tenBe);
}

function updateStudentStars(tenBe, delta) {
  const row = findStudentRow(tenBe);
  if (row < 2) return false;

  const sh = getSheet(SHEET_HOCSINH);
  const current = Number(sh.getRange(row, 3).getValue() || 0);
  let next = current + Number(delta || 0);

  if (next < 0) next = 0;

  sh.getRange(row, 3).setValue(next);
  return next;
}

/*************************************************
 * 📚 TOPICS
 *************************************************/
function getTopicsFromSheet(sheetName) {
  const sh = getSheet(sheetName);
  const data = sh.getDataRange().getValues();
  if (data.length <= 1) return [];

  const set = {};
  data.slice(1).forEach(r => {
    const topic = String(r[3] || "").trim();
    if (topic) set[topic] = true;
  });

  return Object.keys(set);
}

/*************************************************
 * 📘 CÂU HỎI
 *************************************************/
function getQuestions(mon, tuoi, soCau, topicsSelected) {
  ensureAllSheets();

  const sheetName =
    mon === "Toán" ? SHEET_TOAN :
    mon === "Tiếng Việt" ? SHEET_TV :
    SHEET_ANH;

  const sh = getSheet(sheetName);
  const data = sh.getDataRange().getValues();
  if (data.length <= 1) return { questions: [], allAnswers: [] };

  let list = data.slice(1).filter(r => r[0] && r[1]).map(r => ({
    cauhoi: r[0],
    dapandung: r[1],
    tuoi: Number(r[2] || 0),
    chude: r[3] || "",
    hinhAnh: r[4] || ""
  }));

  // Không phụ thuộc tuổi nếu không khớp
  let filteredByAge = list;
  if (tuoi) {
    filteredByAge = list.filter(q => !q.tuoi || Number(q.tuoi) === Number(tuoi));
    if (filteredByAge.length) list = filteredByAge;
  }

  if (topicsSelected && topicsSelected.length) {
    const filteredTopic = list.filter(q => topicsSelected.includes(q.chude));
    if (filteredTopic.length) list = filteredTopic;
  }

  list = shuffleArray(list);

  const count = Math.min(Number(soCau || 10), list.length);
  const picked = list.slice(0, count);

  return {
    questions: picked,
    allAnswers: [...new Set(list.map(x => String(x.dapandung).trim()).filter(Boolean))]
  };
}

function shuffleArray(arr) {
  const a = [...arr];
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}

/*************************************************
 * 💾 LƯU KẾT QUẢ
 *************************************************/
function saveResult(payload) {
  ensureAllSheets();

  const sh = getSheet(SHEET_KETQUA);
  const tenBe = payload.tenBe || "";
  const tuoi = payload.tuoi || "";
  const mon = payload.mon || "";
  const mode = payload.mode || "Tự luyện";
  const results = payload.results || [];

  let totalDelta = 0;
  const rows = [];

  results.forEach(r => {
    const saoNhan = Number(r.saoThucNhan || 0);
    totalDelta += saoNhan;

    rows.push([
      new Date(),
      tenBe,
      tuoi,
      mon,
      mode,
      r.cauhoi || "",
      r.dapandung || "",
      r.traloi || "",
      r.ketqua || "",
      saoNhan
    ]);
  });

  if (rows.length) {
    sh.getRange(sh.getLastRow() + 1, 1, rows.length, rows[0].length).setValues(rows);
  }

  updateStudentStars(tenBe, totalDelta);

  // cộng exp pet mặc định
  addPetExpForStudy(tenBe, results.filter(x => x.ketqua === "Đúng").length * 5);

  return { success: true };
}

/*************************************************
 * 🎁 KHO QUÀ
 *************************************************/
function getRewardCatalog() {
  return [
    { name: "🍭 Kẹo ngọt", stars: 100 },
    { name: "🍫 Socola", stars: 150 },
    { name: "🧸 Gấu bông nhỏ", stars: 200 },
    { name: "🎨 Bộ tô màu", stars: 300 },
    { name: "📚 Truyện tranh", stars: 400 },
    { name: "🚗 Xe đồ chơi", stars: 500 },
    { name: "🪀 Đồ chơi vui nhộn", stars: 1000 },
    { name: "🎁 Hộp quà lớn", stars: 2000 },
    { name: "🏆 Siêu quà VIP", stars: 5000 }
  ];
}

function getUserRewardData(tenBe) {
  const hs = getStudentByName(tenBe);
  if (!hs) return { sao: 0, qua: "", rewardCatalog: getRewardCatalog() };

  return {
    sao: Number(hs.sao || 0),
    qua: hs.qua || "",
    rewardCatalog: getRewardCatalog()
  };
}

function redeemReward(tenBe, stars, rewardName) {
  const row = findStudentRow(tenBe);
  if (row < 2) return { success: false, message: "Không tìm thấy học sinh" };

  const sh = getSheet(SHEET_HOCSINH);
  const currentStars = Number(sh.getRange(row, 3).getValue() || 0);
  const currentRewards = String(sh.getRange(row, 4).getValue() || "").trim();

  if (currentStars < Number(stars)) {
    return { success: false, message: "Không đủ sao" };
  }

  const newStars = currentStars - Number(stars);
  const rewards = currentRewards ? currentRewards.split(",").map(x => x.trim()).filter(Boolean) : [];
  rewards.push(rewardName);

  sh.getRange(row, 3).setValue(newStars);
  sh.getRange(row, 4).setValue(rewards.join(", "));

  return { success: true, message: "Đổi quà thành công" };
}

function clearReward(tenBe, rewardName) {
  const row = findStudentRow(tenBe);
  if (row < 2) return { success: false };

  const sh = getSheet(SHEET_HOCSINH);
  const currentRewards = String(sh.getRange(row, 4).getValue() || "").trim();
  const rewards = currentRewards ? currentRewards.split(",").map(x => x.trim()).filter(Boolean) : [];
  const filtered = rewards.filter(x => x !== rewardName);

  sh.getRange(row, 4).setValue(filtered.join(", "));
  return { success: true };
}
/*************************************************
 * 🐾 PET
 *************************************************/
function getAllPetCatalog() {
  const sh = getSheet(SHEET_PETS);
  const data = sh.getDataRange().getValues();
  if (data.length <= 1) return [];

  return data.slice(1).filter(r => r[0]).map(r => ({
    id: r[0],
    name: r[1],
    emoji: r[2],
    price: Number(r[3] || 0),
    rarity: r[4] || "Thường",
    baseAtk: Number(r[5] || 10),
    baseHp: Number(r[6] || 100),
    skill: r[7] || "Đánh thường",
    skillType: r[8] || "magic"
  }));
}

function getOwnedPetsRaw(tenBe) {
  const hs = getStudentByName(tenBe);
  if (!hs) return [];

  try {
    const parsed = JSON.parse(hs.petsJson || "[]");
    return Array.isArray(parsed) ? parsed : [];
  } catch (e) {
    return [];
  }
}

function saveOwnedPetsRaw(tenBe, arr) {
  const row = findStudentRow(tenBe);
  if (row < 2) return false;

  getSheet(SHEET_HOCSINH).getRange(row, 5).setValue(JSON.stringify(arr || []));
  return true;
}

function getFullPetInfoForUser(tenBe) {
  const catalog = getAllPetCatalog();
  const ownedRaw = getOwnedPetsRaw(tenBe);

  return catalog.map(p => {
    const own = ownedRaw.find(x => x.id === p.id);
    return {
      ...p,
      owned: !!own,
      level: own ? Number(own.level || 1) : 1,
      exp: own ? Number(own.exp || 0) : 0,
      evolution: own ? Number(own.evolution || 1) : 1,
      fashion: own ? String(own.fashion || "Mặc định") : "Mặc định",
      owner: tenBe
    };
  });
}

function buyPetForUser(tenBe, petId) {
  const catalog = getAllPetCatalog();
  const pet = catalog.find(x => x.id === petId);
  if (!pet) return { success: false, message: "Không tìm thấy pet" };

  const owned = getOwnedPetsRaw(tenBe);
  if (owned.find(x => x.id === petId)) {
    return { success: false, message: "Bạn đã sở hữu pet này rồi" };
  }

  const hs = getStudentByName(tenBe);
  if (!hs) return { success: false, message: "Không tìm thấy học sinh" };

  if (Number(hs.sao || 0) < Number(pet.price || 0)) {
    return { success: false, message: "Không đủ sao để mua pet" };
  }

  updateStudentStars(tenBe, -pet.price);

  owned.push({
    id: pet.id,
    level: 1,
    exp: 0,
    evolution: 1,
    fashion: "Mặc định",
    ownedAt: new Date().toISOString()
  });

  saveOwnedPetsRaw(tenBe, owned);
  return { success: true, message: `🎉 Đã mua ${pet.name}!` };
}

function deleteOwnedPet(tenBe, petId) {
  if (petId === "pet_001") {
    return { success: false, message: "Không thể xoá pet mặc định" };
  }

  let owned = getOwnedPetsRaw(tenBe);
  const before = owned.length;
  owned = owned.filter(x => x.id !== petId);

  if (owned.length === before) {
    return { success: false, message: "Không tìm thấy pet để xoá" };
  }

  saveOwnedPetsRaw(tenBe, owned);
  return { success: true, message: "🗑️ Đã xoá pet khỏi bộ sưu tập" };
}

function feedOrPlayPet(tenBe, petId, actionType) {
  const owned = getOwnedPetsRaw(tenBe);
  const pet = owned.find(x => x.id === petId);
  if (!pet) return { success: false, message: "Không tìm thấy pet" };

  let addExp = 5;
  let cost = 1;

  if (actionType === "feed") {
    addExp = 5;
    cost = 1;
  }
  if (actionType === "play") {
    addExp = 8;
    cost = 2;
  }
  if (actionType === "train") {
    addExp = 12;
    cost = 3;
  }

  const hs = getStudentByName(tenBe);
  if (!hs) return { success: false, message: "Không tìm thấy học sinh" };

  if (Number(hs.sao || 0) < cost) {
    return { success: false, message: `Không đủ sao. Cần ${cost} sao.` };
  }

  updateStudentStars(tenBe, -cost);

  pet.exp = Number(pet.exp || 0) + addExp;
  levelUpPet(pet);
  saveOwnedPetsRaw(tenBe, owned);

  return { success: true, message: `✨ Thành công! -${cost} sao, +${addExp} EXP` };
}

function levelUpPet(pet) {
  let loopSafe = 0;
  while (loopSafe < 50) {
    const need = 30 + (Number(pet.level || 1) - 1) * 20;
    if (Number(pet.exp || 0) >= need) {
      pet.exp -= need;
      pet.level = Number(pet.level || 1) + 1;
    } else {
      break;
    }
    loopSafe++;
  }
}

function evolvePet(tenBe, petId) {
  const owned = getOwnedPetsRaw(tenBe);
  const pet = owned.find(x => x.id === petId);
  if (!pet) return { success: false, message: "Không tìm thấy pet" };

  if (Number(pet.level || 1) < 5) {
    return { success: false, message: "Pet cần đạt cấp 5 mới tiến hoá được!" };
  }

  pet.evolution = Number(pet.evolution || 1) + 1;
  pet.level = 1;
  pet.exp = 0;

  saveOwnedPetsRaw(tenBe, owned);
  return { success: true, message: "🧬 Pet đã tiến hoá thành công!" };
}

function setPetFashion(tenBe, petId, fashionName) {
  const owned = getOwnedPetsRaw(tenBe);
  const pet = owned.find(x => x.id === petId);
  if (!pet) return { success: false };

  pet.fashion = fashionName || "Mặc định";
  saveOwnedPetsRaw(tenBe, owned);
  return { success: true };
}

function addPetExpForStudy(tenBe, amount) {
  const owned = getOwnedPetsRaw(tenBe);
  if (!owned.length) return;

  owned[0].exp = Number(owned[0].exp || 0) + Number(amount || 0);
  levelUpPet(owned[0]);
  saveOwnedPetsRaw(tenBe, owned);
}

/*************************************************
 * ⚔️ BATTLE
 *************************************************/
function getBattlePlayers() {
  return getHocSinhData();
}

function simulateBattle(playerName, enemyName, playerPetId, enemyPetId) {
  const playerPets = getFullPetInfoForUser(playerName);
  const enemyPets = getFullPetInfoForUser(enemyName);

  const playerPet = playerPets.find(x => x.id === playerPetId && x.owned);
  const enemyPet = enemyPets.find(x => x.id === enemyPetId && x.owned);

  if (!playerPet || !enemyPet) {
    return { success: false, message: "Không tìm thấy pet chiến đấu." };
  }

  const p1 = buildBattlePet(playerPet, playerName);
  const p2 = buildBattlePet(enemyPet, enemyName);

  const logs = [];
  let turn = 0;

  while (p1.hp > 0 && p2.hp > 0 && turn < 50) {
    turn++;

    let dmg1 = calculateDamage(p1, p2);
    p2.hp = Math.max(0, p2.hp - dmg1);
    logs.push({
      attacker: playerName,
      pet: p1.name,
      skill: p1.skill,
      skillType: p1.skillType,
      damage: dmg1,
      targetHp: p2.hp
    });
    if (p2.hp <= 0) break;

    let dmg2 = calculateDamage(p2, p1);
    p1.hp = Math.max(0, p1.hp - dmg2);
    logs.push({
      attacker: enemyName,
      pet: p2.name,
      skill: p2.skill,
      skillType: p2.skillType,
      damage: dmg2,
      targetHp: p1.hp
    });
  }

  const winner = p1.hp > 0 ? playerName : enemyName;
  const loser = winner === playerName ? enemyName : playerName;
  const rewardStars = 5;

  updateBattleStats(winner, loser);
  updateStudentStars(winner, rewardStars);

  return {
    success: true,
    winner,
    rewardStars,
    logs,
    playerPet: {
      owner: playerName,
      name: p1.name,
      emoji: p1.emoji,
      hp: p1.maxHp
    },
    enemyPet: {
      owner: enemyName,
      name: p2.name,
      emoji: p2.emoji,
      hp: p2.maxHp
    }
  };
}

function buildBattlePet(p, owner) {
  const level = Number(p.level || 1);
  const evo = Number(p.evolution || 1);

  const maxHp = Number(p.baseHp || 100) + level * 12 + (evo - 1) * 20;
  const atk = Number(p.baseAtk || 10) + level * 3 + (evo - 1) * 5;

  return {
    owner,
    id: p.id,
    name: p.name,
    emoji: p.emoji,
    skill: p.skill,
    skillType: p.skillType,
    atk,
    hp: maxHp,
    maxHp
  };
}

function calculateDamage(attacker, defender) {
  const rand = Math.floor(Math.random() * 8);
  return Math.max(5, attacker.atk + rand);
}

function updateBattleStats(winnerName, loserName) {
  const sh = getSheet(SHEET_HOCSINH);
  const winnerRow = findStudentRow(winnerName);
  const loserRow = findStudentRow(loserName);

  if (winnerRow >= 2) {
    const w = Number(sh.getRange(winnerRow, 6).getValue() || 0);
    sh.getRange(winnerRow, 6).setValue(w + 1);
  }

  if (loserRow >= 2) {
    const l = Number(sh.getRange(loserRow, 7).getValue() || 0);
    sh.getRange(loserRow, 7).setValue(l + 1);
  }
}

/*************************************************
 * 👨‍👩‍👧 PARENT
 *************************************************/
function parentAdjustStars(tenBe, soSao, ghiChu) {
  const delta = Number(soSao || 0);
  const saoMoi = updateStudentStars(tenBe, delta);

  const sh = getSheet(SHEET_PARENT_LOG);
  sh.appendRow([
    new Date(),
    tenBe,
    delta,
    ghiChu || "",
    saoMoi
  ]);

  return {
    success: true,
    saoMoi: saoMoi
  };
}