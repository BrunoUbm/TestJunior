<template>
    <div style="height: 100vh" @click="DefinedCircle">
        <div class="options">
            <div class="remove" @click="ElementDelet">Excluir</div>
            <div class="volver" @click="ReturnElement">Voltar</div>
        </div>
        <div class="point" v-for="pt in points" :key="pt" ></div>
    </div>
</template>

<script>


export default {
    data() {
        return{
            points: [],
            excluded: []
        }
    },
    methods: {
        DefinedCircle(a) {
            this.excluded = []

            class PointPosition {
                constructor(X, Y) {
                    this.X = X,
                    this.Y = Y
                }
            }
            const ClientResult = new PointPosition(a.clientX, a.clientY)
            console.log(ClientResult);
            const RenderCircle = () => {
                this.points.unshift(ClientResult)
                for(let i of this.points){
                    const circle = {
                        positionX: document.querySelector('.point').style.left = `${i.X}px`, 
                        positionY: document.querySelector('.point').style.top = `${i.Y}px` 
                    }
                    return circle
                }
            }
            RenderCircle()

  },
        ElementDelet(b) {
            b.stopPropagation()
            const RemoveElement = () => {
                this.excluded.unshift(this.points[0])
                this.points.splice(0, 1)
            }
            RemoveElement()
        },

        ReturnElement(c) {
            c.stopPropagation()
            const ElementVolver = () => {
                this.points.unshift(this.excluded[0])
                this.excluded.splice(0, 1)
                for(let item of this.points){
                const returncircle = {
                    positionX: document.querySelector('.point').style.left = `${item.X}px`, 
                    positionY: document.querySelector('.point').style.top = `${item.Y}px` 
                 }
                 console.log(this.points);
                 return returncircle
            }
            }
            ElementVolver()
        }
    }
}


</script>

<style>
.point{
    height: 30px;
    width: 30px;
    border-radius: 50%;
    background: rgb(0, 255, 8);
    position: absolute;
}
.options{
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    color: rgb(98, 68, 68);
    margin-top: 20px;
}
.remove{
    padding: 20px;
    font-size: 25px;
    background: wheat;
    border-radius: 5px;
    cursor: pointer;
    background: rgb(0, 161, 0);
    color: white;
}
.remove:hover{
    transform: scale(1.1);
    background: rgb(0, 255, 0);
}
.volver{
    padding: 20px;
    background: wheat;
    font-size: 25px;
    border-radius: 5px;
    cursor: pointer;
    background: rgb(0, 161, 0);
    color: white;
}
.volver:hover{
    transform: scale(1.1);
    background: rgb(0, 255, 0);
}
</style>