[Home](README.md) | [Projects](projects.md) | [Reflections](reflections.md) | [Codes](codes.md) | [Videos](videos.md) | [To-do](To-do.md) | [Review](review.md)

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

<h2>SpinnerSimulationNested ConditionalsVersion Code</h2>
import SwiftUI

struct ContentView: View {
    @State private var currentColor: Color = .gray
    @State private var colorName: String = "Gray"
    
    var body: some View {
        VStack(spacing: 30) {
            Text("Spinner Simulation")
                .font(.largeTitle)
            
            ZStack {
                Rectangle()
                    .fill(currentColor)
                    .frame(width: 200, height: 200)
                    .cornerRadius(20)
                
                Text(colorName)
                    .font(.title)
                    .foregroundColor(.white)
            }
            
            Button("Spin") {
                spin()
            }
            .padding()
            .background(Color.black.opacity(0.1))
            .cornerRadius(10)
        }
        .padding()
    }
    
    func spin() {
        let first = Int.random(in: 1...2)
        
        if first == 1 {
            currentColor = .blue
            colorName = "Blue"
        } else {
            let second = Int.random(in: 1...2)
            
            if second == 1 {
                currentColor = .orange
                colorName = "Orange"
            } else {
                currentColor = .purple
                colorName = "Purple"
            }
        }
    }
}

<h2>Robot Movement Simulation</h2>
import SwiftUI

struct ContentView: View {
    @State var y:CGFloat = 0
    @State var x:CGFloat = 0
    @State var color = [Color.green, Color.blue, Color.gray]
    @State var currentIndex = 0
    
    func moveup () {y = y - 5 }
    func movedown () {y = y + 5 }
    func moveright () {x = x + 5 }
    func moveleft () {x = x - 5 }
    func changeColor () {
        currentIndex = (currentIndex + 1) % color.count
    }
    
    var body: some View {
        VStack {
            Rectangle()
                .fill(color[currentIndex])
                .frame(width: 50, height: 50)
                .offset(x: x, y: y)
            ZStack {
                Button("⬅️") {moveleft() }
                .offset(x: -30, y: 300)
                Button("⬆️") { moveup() }
                .offset(x: 0, y: 270)
                Button("⬇️") { movedown() }
                .offset(x: 0, y: 330)
                Button("➡️") { moveright() }
                .offset(x: 30, y: 300)
            }
            Button("Change Color") {
                changeColor()
            }
            .frame(width: 75, height: 50)
            .background(color[currentIndex])
            .cornerRadius(10)
            .offset(x: 0, y: 360)
        }
    }
}



<h2>Rock paper scissors</h2>

import SwiftUI

struct ContentView: View {
    
    let choices = ["🪨", "📄", "✂️"]
    
    @State private var computerChoice = "❓"
    @State private var result = "Make your choice"
    
    func play(userChoice: String) {
        let randomIndex = Int.random(in: 0..<choices.count)
        computerChoice = choices[randomIndex]
        
        if userChoice == computerChoice {
            result = "It's a tie!"
        }
        else if (userChoice == "🪨" && computerChoice == "✂️") ||
                    (userChoice == "📄" && computerChoice == "🪨") ||
                    (userChoice == "✂️" && computerChoice == "📄") {
            result = "You win!"
        }
        else {
            result = "You lose!"
        }
    }
    
    var body: some View {
        VStack(spacing: 30) {
            
            Text("Rock Paper Scissors")
                .font(.largeTitle)
            
            Text("Computer: \(computerChoice)")
                .font(.title)
            
            Text(result)
                .font(.title2)
            
            HStack(spacing: 20) {
                ForEach(choices, id: \.self) { choice in
                    Button(choice) {
                        play(userChoice: choice)
                    }
                    .font(.largeTitle)
                }
            }
        }
        .padding()
    }
}


<h2>Binary Search</h2>

import SwiftUI

struct ContentView: View {
    let database = [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
    let targetID = 23
    
    @State private var output: [String] = []
    
    var body: some View {
        VStack(alignment: .leading, spacing: 5) {
            ForEach(output, id: \.self) { line in
                Text(line)
                    .font(.system(.body, design: .monospaced))
            }
            
            Button("Run Binary Search") {
                runBinarySearch()
            }
            .padding(.top, 20)
        }
        .padding()
    }
    
    func runBinarySearch() {
        output.removeAll()
        
        var low = 0
        var high = database.count - 1
        var steps = 0
        var found = false
        
        output.append("> SYSTEM: Starting Binary Search Protocol...")
        output.append("> Target ID: \(targetID)")
        output.append("> ---------------------------------------------")
        
        while low <= high && !found {
            steps += 1
            let mid = (low + high) / 2
            output.append("> Step \(steps): Checking Index [\(mid)] -> Value: \(database[mid])")
            
            if database[mid] == targetID {
                found = true
                output.append("> ")
                output.append(">  SUCCESS: User ID found at Index \(mid)")
                output.append(">  EFFICIENCY: Operation completed in \(steps) steps.")
            } else if database[mid] < targetID {
                low = mid + 1
            } else {
                high = mid - 1
            }
        }
    }
}

#Preview {
    ContentView()
}

