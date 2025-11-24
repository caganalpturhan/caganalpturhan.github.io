[Home](README.md) | [Projects](projects.md) | [Reflections](reflections.md) | [Codes](codes.md) | [Videos](videos.md)

<h2>Swift Design Challeng V1</h2>
import SwiftUI

struct ContentView: View {
    let aiTopics = [
        "🤖 Machine Learning",
        "🧠 Neural Networks",
        "📊 Data Analysis",
        "💬 Natural Language Processing",
        "🎨 AI Creativity"
    ]
    
    var body: some View {
        NavigationView {
            VStack(alignment: .leading, spacing: 16) {
                Text("AI")
                    .font(.largeTitle)
                    .fontWeight(.bold)
                
                Text("Key topics in artificial intelligence")
                    .font(.subheadline)
                    .foregroundColor(.gray)
                
                List(aiTopics, id: \.self) { topic in
                    Text(topic)
                        .font(.body)
                }
                .listStyle(InsetGroupedListStyle())
            }
            .padding()
            .navigationBarHidden(true)
        }
    }
}







struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

<h2>List Project Icecream</h2>
import SwiftUI

struct ContentView: View {
    let flavors = ["Vanilla", "Chocolate", "Strawberry"]
    let scoops = [2, 3, 1]
    
    var body: some View {
        VStack {
            Text("🍦 Ice Cream List").font(.title)
            
            ForEach(0..<flavors.count, id: \.self) { i in
                Text("\(flavors[i]) - \(scoops[i]) scoops")
            }
        }
        .padding()
    }
}


<h2>World Clock V1</h2>
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack(alignment: .leading, spacing: 10) {
            Text("World Clock")
                .font(.title)
                .bold()
                .padding(.bottom, 10)
            
            HStack {
                Text("City")
                    .bold()
                    .frame(width: 100, alignment: .leading)
                Text("Time")
                    .bold()
            }
            
            let cities = [
                ("🇯🇵Tokyo", 6),
                ("🇫🇷Paris", -1),
                ("🇺🇸NewYork", -7),
                ("🇰🇷Seoul", 6),
                ("🇦🇺Sydney", 7),
                ("🇹🇷Ankara", 0)
            ]
            
            let turkeyTime = 12
            
            ForEach(cities, id: \.0) { city, offset in
                HStack {
                    Text(city)
                        .frame(width: 100, alignment: .leading)
                    let localTime = (turkeyTime + offset + 24) % 24
                    Text("\(localTime):00")
                }
            }
        }
        .padding()
    }
}


<h2>Pixel Painter</h2>
1. Create a list called "cells" with numbers 0–99.
2. Create a list called "cellColors" with 100 items.

3. Function drawGrid():
    For each row from 0 to 9:
        For each column from 0 to 9:
            index = row * 10 + column
            Draw a square at this position
            Fill the square with cellColors[index]

4. Function changeColor(inputNumber):
    If inputNumber >= 0 AND inputNumber <= 99:
        cellColors[inputNumber] = blue
    Else:
        print "Wrong input"

5. Display a TextField for the user to type a number
6. Display a Button that calls changeColor() with the input number
7. Call drawGrid() to show the updated grid

import SwiftUI

struct ContentView: View {
    @State private var cells = Array(0...99)
    @State private var cellColors = Array(repeating: Color.gray, count: 100)
    @State private var inputNumber = ""
    
    var body: some View {
        VStack {
            drawGrid()
            
            HStack {
                TextField("0-99", text: $inputNumber)
                    .textFieldStyle(RoundedBorderTextFieldStyle())
                    .frame(width: 60)
                Button("Color") {
                    changeColor()
                }
            }
            .padding()
        }
        .padding()
    }
    
    func drawGrid() -> some View {
        VStack(spacing: 2) {
            ForEach(0..<10, id: \.self) { row in
                HStack(spacing: 2) {
                    ForEach(0..<10, id: \.self) { col in
                        let index = row * 10 + col
                        Rectangle()
                            .fill(cellColors[index])
                            .frame(width: 30, height: 30)
                            .border(Color.black)
                    }
                }
            }
        }
    }
    
    func changeColor() {
        if let number = Int(inputNumber), number >= 0, number <= 99 {
            cellColors[number] = .blue
        } else {
            print("Invalid input")
        }
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

