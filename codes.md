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



