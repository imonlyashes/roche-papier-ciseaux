<script> 
    export default {
        data() {
            return {
                choixOrdi: '',
                choixPossibles: ['Roche', 'Papier', 'Ciseaux'],
                scoreJoueur: 0
            }
        },
        methods: {
            ordiPick(){
                this.choixOrdi = this.choixPossibles[Math.floor(Math.random() * (this.choixPossibles.length - 1))]
                return this.choixOrdi
            },
            ordiRoche(){
                this.$refs.ordi.style.display = "block"
                this.$refs.choixOrdiHtml.textContent = "roche"
                this.$refs.choixOrdiHtml.style.color = "#976297"
                this.$refs.choixOrdiHtml.style.fontWeight = "bold"
            },
            ordiPapier(){
                this.$refs.ordi.style.display = "block"
                this.$refs.choixOrdiHtml.textContent = "papier"
                this.$refs.choixOrdiHtml.style.color = "#00A19A"
                this.$refs.choixOrdiHtml.style.fontWeight = "bold"
            },
            ordiCiseaux(){
                this.$refs.ordi.style.display = "block"
                this.$refs.choixOrdiHtml.textContent = "ciseaux"
                this.$refs.choixOrdiHtml.style.color = "#EC8B41"
                this.$refs.choixOrdiHtml.style.fontWeight = "bold"
            },
            resultatNull(){
                this.$refs.resultat.style.display = "block"
                this.$refs.resultat.textContent = "NULL"
                this.$refs.resultat.style.color = "#EFD135"
                this.scoreJoueur = this.scoreJoueur;
                this.$refs.scoreJoueurHtml.textContent = this.scoreJoueur
            },
            resultatPerdu() {
                this.$refs.resultat.style.display = "block"
                this.$refs.resultat.textContent = "PERDU"
                this.$refs.resultat.style.color = "#FF3838"
                this.scoreJoueur = 0;
                this.$refs.scoreJoueurHtml.textContent = this.scoreJoueur
            },
            resultatGagne(){
                this.$refs.resultat.style.display = "block"
                this.$refs.resultat.textContent = "GAGNÉ"
                this.$refs.resultat.style.color = "#41BA3F"
                this.scoreJoueur = this.scoreJoueur + 1
                this.$refs.scoreJoueurHtml.textContent = this.scoreJoueur
            },
            joueurChoixRoche(){
                this.$refs.roche.style.opacity = "1"
                this.$refs.papier.style.opacity = "0.2"
                this.$refs.ciseaux.style.opacity = "0.2"
                this.$refs.faireChoix.style.display = "none"
                this.$refs.joueur.style.display = "block"

                this.$refs.choixJoueurHtml.textContent = "roche"
                this.$refs.choixJoueurHtml.style.color = "#976297"
                this.$refs.choixJoueurHtml.style.fontWeight = "bold"

                this.$refs.btnRejouer.style.display = "block"

                this.ordiPick()

                if(this.choixOrdi === this.choixPossibles[0]){
                    this.ordiRoche()
                    this.resultatNull()
                } 
                else if (this.choixOrdi === this.choixPossibles[1]) {
                    this.ordiPapier()
                    this.resultatPerdu()
                } 
                else {
                    this.ordiCiseaux()
                    this.resultatGagne()
                }
            },
            joueurChoixPapier(){
                this.$refs.roche.style.opacity = "0.2"
                this.$refs.papier.style.opacity = "1"
                this.$refs.ciseaux.style.opacity = "0.2"
                this.$refs.faireChoix.style.display = "none"
                this.$refs.joueur.style.display = "block"

                this.$refs.choixJoueurHtml.textContent = "papier"
                this.$refs.choixJoueurHtml.style.color = "#00A19A"
                this.$refs.choixJoueurHtml.style.fontWeight = "bold"

                this.$refs.btnRejouer.style.display = "block"

                this.ordiPick();

                if(this.choixOrdi === this.choixPossibles[0]){
                    this.ordiRoche()
                    this.resultatGagne()
                } 
                else if (this.choixOrdi === this.choixPossibles[1]) {
                    this.ordiPapier()
                    this.resultatNull()
                } 
                else {
                    this.ordiCiseaux()
                    this.resultatPerdu()
                }
            },
            joueurChoixCiseaux(){
                this.$refs.roche.style.opacity = "0.2"
                this.$refs.papier.style.opacity = "0.2"
                this.$refs.ciseaux.style.opacity = "1"
                this.$refs.faireChoix.style.display = "none"
                this.$refs.joueur.style.display = "block"

                this.$refs.choixJoueurHtml.textContent = "ciseaux"
                this.$refs.choixJoueurHtml.style.color = "#EC8B41"
                this.$refs.choixJoueurHtml.style.fontWeight = "bold"

                this.$refs.btnRejouer.style.display = "block"

                this.ordiPick()

                if(this.choixOrdi === this.choixPossibles[0]){
                    this.ordiRoche()
                    this.resultatPerdu()
                } 
                else if (this.choixOrdi === this.choixPossibles[1]) {
                    this.ordiPapier()
                    this.resultatGagne()
                } 
                else {
                    this.ordiCiseaux()
                    this.resultatNull()
                }
            },
            rejouer(){
                this.$refs.btnRejouer.style.display = "none"
                this.$refs.roche.style.opacity = "1"
                this.$refs.papier.style.opacity = "1"
                this.$refs.ciseaux.style.opacity = "1"
                this.$refs.faireChoix.style.display = "block"
                this.$refs.joueur.style.display = "none"
                this.$refs.ordi.style.display = "none"
                this.$refs.resultat.style.display = "none"
                choixOrdi = ''
            }
        }
    }
</script>

<template>
    <p ref="faireChoix">Faites votre choix en cliquant sur l'icône désirée</p>
        <p id="joueur" ref="joueur">Vous avez choisi <span ref="choixJoueurHtml"></span></p>

        <div>
            <img src="../assets/img/roche.svg" alt="Illustration d'une main dont le poing est fermé" ref="roche" @click="joueurChoixRoche()">
            <img src="../assets/img/papier.svg" alt="Illustration d'une main ouverte" ref="papier" @click="joueurChoixPapier()">
            <img src="../assets/img/ciseaux.svg" alt="Illustration d'une main dont les doigts sont repliés sauf l'index et le majeur" ref="ciseaux" @click="joueurChoixCiseaux()">
        </div>

        <p id="ordi" ref="ordi">Votre adversaire a choisi <span ref="choixOrdiHtml"></span></p>

        <p id="resultat" ref="resultat"></p>

        <p id="score">Score : <span ref="scoreJoueurHtml">0</span></p>

        <button ref="btnRejouer" @click="rejouer()">Rejouer</button>
</template>

<style scoped>
    #joueur, #ordi {
        display: none;
    }

    div {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        width: 80vw;
        margin: 50px auto;
    }

    img {
        width: 30%;
        cursor: pointer;
    }

    #resultat {
        font-size: 2.5rem;
        margin: 30px 0;
        text-transform: uppercase;
        font-weight: bold;
        display: none;
    }

    #score {
        font-size: 0.8rem;
        font-weight: bold;
    }

    button {
        border: none;
        background-color: white;
        color: #111111;
        padding: 15px;
        width: 250px;
        border-radius: 30px;
        font-size: 0.8rem;
        font-weight: bold;
        text-transform: uppercase;
        margin: 30px auto;
        display: none;
        cursor: pointer;
    }

    @media screen and (min-width: 1024px){
        div {
            width: 60vw;
        }
}
</style>