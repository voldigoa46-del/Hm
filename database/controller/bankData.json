const fs = require('fs');
const path = path.join(__dirname, '../bankData.json');

// Initialisation du fichier JSON s'il n'existe pas
if (!fs.existsSync(path)) {
    fs.writeFileSync(path, JSON.stringify({}));
}

const bankData = {
    // Récupérer les données d'un utilisateur
    get: async function(senderID) {
        const data = JSON.parse(fs.readFileSync(path));
        return data[senderID] || null;
    },

    // Sauvegarder les données d'un utilisateur
    set: async function(senderID, data) {
        const allData = JSON.parse(fs.readFileSync(path));
        allData[senderID] = data;
        fs.writeFileSync(path, JSON.stringify(allData, null, 2));
        return true;
    },

    // Créer un nouveau compte avec la structure par défaut
    create: async function(senderID) {
        const defaultData = {
            balance: 0,
            savings: 0,
            vault: 0,
            loan: 0,
            loanDate: null,
            creditScore: 600,
            bankLevel: 1,
            multiplier: 1,
            premium: false,
            streak: 0,
            reputation: 0,
            lastInterest: Date.now(),
            lastDaily: 0,
            lastWork: 0,
            frozen: false,
            stocks: {},
            crypto: {},
            bonds: {},
            businesses: [],
            realEstate: [],
            vehicles: [],
            luxury: [],
            transactions: [],
            achievements: [],
            skills: {
                gambling: 0,
                trading: 0,
                business: 0,
                investing: 0
            }
        };
        await this.set(senderID, defaultData);
        return defaultData;
    }
};

module.exports = { bankData };
